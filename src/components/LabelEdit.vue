<template>
  <div class="vlabeledit">
    <div class="vlabeledit-label" v-if="!edit">
      {{ vlabel }}
      <span class="edit-icon" @click="onLabelClick">
        <svg viewBox="0 0 24 24" id="ic_edit_24px">
          <path
            d="M3 17.25V21h3.75L17.81 9.94l-3.75-3.75L3 17.25zM20.71 7.04a.996.996 0 0 0 0-1.41l-2.34-2.34a.996.996 0 0 0-1.41 0l-1.83 1.83 3.75 3.75 1.83-1.83z"
          ></path>
        </svg>
      </span>
    </div>

    <input
      type="text"
      v-if="edit"
      v-model="label"
      ref="labeledit"
      :placeholder="vplaceholder"
      class="vlabeledit-input"
      @keyup.enter="updateText"
    />
    <span class="save-icon" v-if="edit" @click="updateText">
      <svg viewBox="0 0 24 24" id="ic_save_24px">
        <path
          d="M17 3H5a2 2 0 0 0-2 2v14a2 2 0 0 0 2 2h14c1.1 0 2-.9 2-2V7l-4-4zm-5 16c-1.66 0-3-1.34-3-3s1.34-3 3-3 3 1.34 3 3-1.34 3-3 3zm3-10H5V5h10v4z"
        ></path>
      </svg>
    </span>
  </div>
</template>
<script>
export default {
  name: 'LabelEdit',
  data: function () {
    return {
      edit: false,
      label: '',
      empty: '默认文本'
    }
  },
  props: ['text', 'placeholder'],
  methods: {
    initText: function () {
      if (this.text === '' || this.text === undefined) {
        this.label = this.vlabel
      } else {
        this.label = this.text
      }
    },

    onLabelClick: function () {
      this.edit = true
      this.label = this.text
    },
    updateText: function () {
      this.edit = false
      this.$emit('updateText', this.label)
    }
  },
  computed: {
    vplaceholder: function () {
      if (this.placeholder === undefined || this.placeholder === '') {
        return this.empty
      } else {
        return this.placeholder
      }
    },
    vlabel: function () {
      if (this.text === undefined || this.text === '') {
        return this.vplaceholder
      } else {
        return this.label
      }
    }
  },
  mounted: function () {
    this.initText()
  },
  updated: function () {
    var ed = this.$refs.labeledit
    if (ed != null) {
      ed.focus()
    }
  },
  watch: {
    text: function (value) {
      if (value === '' || value === undefined) {
        this.label = this.vplaceholder
      }
    }
  }
}
</script>

<style scoped>
.vlabeledit-input {
  border: solid 1px #42b983;
  border-radius: 3px;
  padding: 2px;
  outline: none;
}

svg {
  width: 20px;
  height: 20px;
  fill:#2c3e50;
  vertical-align: middle;
}

.edit-icon {
 visibility: hidden;
  width: 24px;
  height: 24px;
  cursor: pointer;
}
.save-icon {
  width: 32px;
  height: 32px;
  cursor: pointer;
}

.vlabeledit-label:hover .edit-icon{visibility: visible;}
</style>
