# pc-helper-models

Файлы моделей для программы «Помощник» — офлайн-помощника для Windows 10/11.
Здесь лежат **только модели и их лицензии**. Кода программы в этом репозитории нет.

Модели выложены в релизе [models-v1](../../releases/tag/models-v1). Программа сама скачивает
нужную модель отсюда, а если GitHub недоступен — с Hugging Face.

## Модели

| Файл | Исходная модель | Квантование (откуда взято) | Лицензия |
|---|---|---|---|
| `Qwen3-0.6B-Q4_K_M.gguf` | [Qwen/Qwen3-0.6B](https://huggingface.co/Qwen/Qwen3-0.6B) | [unsloth/Qwen3-0.6B-GGUF](https://huggingface.co/unsloth/Qwen3-0.6B-GGUF) | Apache 2.0 |
| `Qwen3-1.7B-Q4_K_M.gguf` | [Qwen/Qwen3-1.7B](https://huggingface.co/Qwen/Qwen3-1.7B) | [unsloth/Qwen3-1.7B-GGUF](https://huggingface.co/unsloth/Qwen3-1.7B-GGUF) | Apache 2.0 |
| `Qwen3-4B-Instruct-2507-Q4_K_M.gguf` | [Qwen/Qwen3-4B-Instruct-2507](https://huggingface.co/Qwen/Qwen3-4B-Instruct-2507) | [unsloth/Qwen3-4B-Instruct-2507-GGUF](https://huggingface.co/unsloth/Qwen3-4B-Instruct-2507-GGUF) | Apache 2.0 |
| `Qwen3-8B-Q4_K_M.gguf` | [Qwen/Qwen3-8B](https://huggingface.co/Qwen/Qwen3-8B) | [unsloth/Qwen3-8B-GGUF](https://huggingface.co/unsloth/Qwen3-8B-GGUF) | Apache 2.0 |
| `Qwen3-14B-Q4_K_M.gguf` | [Qwen/Qwen3-14B](https://huggingface.co/Qwen/Qwen3-14B) | [unsloth/Qwen3-14B-GGUF](https://huggingface.co/unsloth/Qwen3-14B-GGUF) | Apache 2.0 |

Модели созданы командой Qwen (Alibaba Cloud) и распространяются по лицензии
[Apache License 2.0](https://www.apache.org/licenses/LICENSE-2.0). Файлы GGUF не изменялись:
это те же квантования Q4_K_M, что и на Hugging Face. Текст лицензии лежит в релизе рядом с каждой
моделью (`имя-модели.LICENSE.txt`).

## Большие файлы

GitHub не принимает файлы больше 2 ГБ, поэтому модели крупнее 1,9 ГБ разрезаны на части
`имя.gguf.part1`, `имя.gguf.part2`… Программа склеивает их сама. Вручную в Windows:

```
copy /b Qwen3-8B-Q4_K_M.gguf.part1+Qwen3-8B-Q4_K_M.gguf.part2+Qwen3-8B-Q4_K_M.gguf.part3 Qwen3-8B-Q4_K_M.gguf
```

Затем сверьте SHA256 с файлом `SHA256.txt` из релиза:

```
certutil -hashfile Qwen3-8B-Q4_K_M.gguf SHA256
```
