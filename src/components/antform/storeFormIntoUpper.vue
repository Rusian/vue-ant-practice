<template>
  <div id="components-form-demo-global-state">
    <customized-form
      :username="fields.username"
      @change="handleFormChange"
    />
    <pre class="language-bash">
      {{ JSON.stringify(fields, null, 2) }}
    </pre>
  </div>
</template>

<script>
const CustomizedForm = {
  props: ['username'],
  template: `
    <a-form layout='inline' :form="form">
      <a-form-item label='Username'>
        <a-input
          v-decorator="[
            'username',
            {
              rules: [{ required: true, message: 'Username is required!' }],
            }
          ]"
        />
      </a-form-item>
    </a-form>
  `,
  created () {
    this.form = this.$form.createForm(this, {
      onFieldsChange: (_, changedFields) => {
        this.$emit('change', changedFields);
      },
      mapPropsToFields: () => {
        return {
          username: this.$form.createFormField({
            ...this.username,
            value: this.username.value,
          }),
        };
      },
      onValuesChange (_, values) {
        console.log(values);
      },
    });
  },
  watch: {
    username () {
      this.form.updateFields({
        username: this.$form.createFormField({
          ...this.username,
          value: this.username.value,
        }),
      });
    },
  },
};

export default {
  components: {
    CustomizedForm,
  },
  data () {
    return {
      fields: {
        username: {
          value: 'benjycui',
        },
      },
    };
  },
  methods: {
    handleFormChange (changedFields) {
      console.log('changedFields', changedFields);
      this.fields = { ...this.fields, ...changedFields };
    },
  },
};
</script>
<style>
#components-form-demo-global-state .language-bash {
  max-width: 400px;
  border-radius: 6px;
  margin-top: 24px;
}
</style>