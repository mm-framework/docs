Дескрипторы помогают фиксировать поддерживаемые типы входящих/исходящих данных.

Каждый дескриптор обладаем своим набором параметров и отвечает за определенные типы данных.


## Дескрипторы

::: mmf_meta.descriptors
    selection:
      inherited_members: true
      filters: ["!^_", "!to_file"]
      members: ["DataFrame", "Image", "String", "Integer", "Float", "Bool", "Datetime"]
    rendering:
      members_order: "source"

## Типы

::: mmf_meta.descriptors
    selection:
      inherited_members: true
      filters: ["!^_"]
      members: ["DataFrameFormat", "ImageFormat", "ColorMode"]
    rendering:
      members_order: "source"