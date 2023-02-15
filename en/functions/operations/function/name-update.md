# Changing the name of a function

{% list tabs %}

- Management console

   1. In the [management console]({{ link-console-main }}), go to the folder where you want to change the name of a [function](../../concepts/function.md).
   1. Select **{{ sf-name }}**.
   1. Select a function.
   1. In the upper-right corner, click **Edit**.
   1. In the window that opens, enter the desired function name.
   1. Click **Save**.

- CLI

   {% include [cli-install](../../../_includes/cli-install.md) %}

   {% include [default-catalogue](../../../_includes/default-catalogue.md) %}

   To change the function name, run the command:

   ```
   yc serverless function update <function name> --new-name <new function name>
   ```

   Result:
   ```
   id: b097d9ous3gep99khe83
   folder_id: aoek49ghmknnpj1ll45e
   created_at: "2019-06-06T11:36:48.688Z"
   name: my-beta-function
   labels:
    test: test
   log_group_id: eolv6578frac08uh5h6s
   http_invoke_url: https://functions.yandexcloud.net/b097d9ous3gep99khe83
   status: ACTIVE
   ```

- API

   You can change the function name using the API [update](../../functions/api-ref/Function/update.md) method.

- {{ TF }}

   {% include [terraform-definition](../../../_tutorials/terraform-definition.md) %}

   If you don't have {{ TF }}, [install it and configure the {{ yandex-cloud }} provider](../../../tutorials/infrastructure-management/terraform-quickstart.md#install-terraform).

   To change the name of a function:

   1. Open the {{ TF }} configuration file and edit the `name` field in the fragment with the function description.

      Example function description in the {{ TF }} configuration:

      ```
      resource "yandex_function" "test-function" {
          name               = "test-function"
          description        = "Test function"
          user_hash          = "first-function"
          runtime            = "python37"
          entrypoint         = "main"
          memory             = "128"
          execution_timeout  = "10"
          service_account_id = "<service account ID>"
          tags               = ["my_tag"]
          content {
              zip_filename = "<path to ZIP archive>"
          }
      }
      ```

      For more information about the `yandex_function` resource parameters, see the [provider documentation]({{ tf-provider-link }}/function).

   1. Check the configuration using the command:

      ```
      terraform validate
      ```

      If the configuration is correct, the following message is returned:

      ```
      Success! The configuration is valid.
      ```

   1. Run the command:

      ```
      terraform plan
      ```

      The terminal will display a list of resources with parameters. No changes are made at this step. If the configuration contains errors, {{ TF }} will point them out.

   1. Apply the configuration changes:

      ```
      terraform apply
      ```
   1. Confirm the changes: type `yes` into the terminal and press **Enter**.

   You can verify the function name change using the [management console]({{ link-console-main }}) or this [CLI](../../../cli/quickstart.md) command:

   ```
   yc serverless function list
   ```

- {{ yandex-cloud }} Toolkit

   You can change the function name using the [{{ yandex-cloud }} Toolkit plugin](https://github.com/yandex-cloud/ide-plugin-jetbrains/blob/master/README.en.md) for the IDE family on the [IntelliJ platform](https://www.jetbrains.com/opensource/idea/) from [JetBrains](https://www.jetbrains.com/).

{% endlist %}