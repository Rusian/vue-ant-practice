<template>
  <a-form :form="form">
    <a-form-item
    :wrapper-col="formItemLayout.wrapperEditCol">
      <a-input
        v-decorator="[
        ]"
        placeholder="edit something"
        @keydown.enter="add"
      >
      </a-input>
    </a-form-item>
    <a-row>
      <a-form-item 
      :wrapper-col="formItemLayout.wrapperContentCol"
      >
      <a-checkbox/>
      <a-plain-text></a-plain-text>
      <a-button>
        删除
      </a-button>
      </a-form-item>
    </a-row>


  </a-form>
</template>

<script>
const formItemLayout = {
  wrapperEditCol: { span: 10},
  wrapperContentCol: { span: 25 }
}

export default {
  

  beforecreate () {
    this.form = this.$form.createForm(this);
    this.form.getFieldDecorator('keys', { initialValue: [], preserve: true });
  },
  methods: {
    remove (k) {

    }

  },

  add () {
    const { form } = this;
    const keys = form.getFieldValue('keys');
    const nextKeys = keys.concat(++id);
      // can use data-binding to set
      // important! notify form to detect changes
    form.setFieldsValue({
      keys: nextKeys,
    });
  }

}
</script>

<style>

</style>
