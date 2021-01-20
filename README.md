# devops-netology
Homeworks by course

`.gitignore` для terraform
По данному конфигурационному файлу, будут проигнорированы следующие файлы проекта:
* Все содержимое папки `.terraform`
* Файлы название которых заканчивается (`.tfstate` или `.tfvars`) расширение видимо такое имеют
* Файлы название которых заканчивается (`*_override.tf` или `*_override.tf.json`)
* Файлы в названии которых есть `.tfstate.`
* Файлы `crash.log`, `override.tf`, `override.tf.json` `.terraformrc`
  `terraform.rc`
* В файле так же присутствуют закомментированные настройки `# !example_override.tf` и `# example: *tfplan*`
Они не будут применены.
