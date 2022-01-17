`mmf-meta` - небольшая библиотека для упрощения работы над mmf.yml
## Установка
```shell
pip install mmf-meta
```
## Пример использования
```python
from mmf_meta import mmf

# mmf.artifact работает аналогично стандартному open, только так же помечает файл, который открывает, как артефакт модели
with mmf.artifact('model', 'b', description='Веса модели') as f:   
    model = pickle.load(f)

@mmf.target(
    taskType=mmf.JsonToJson,
    description='Описание функции score',
)
def score(data: dict):
    return model(data)
```
И теперь из консоли можно вызвать:
```shell
mmf-meta main.py
```
В результате чего будет сформирован файл mmf.yml