# pc-helper-models

Файлы моделей для программы «Помощник» — офлайн-помощника для Windows 10/11.
Здесь лежат **только модели и их лицензии**. Кода программы в этом репозитории нет.

Модели выложены в двух релизах. Программа сама скачивает нужные файлы отсюда, а если GitHub недоступен —
с Hugging Face.
- [models-v1](../../releases/tag/models-v1) — модели умного режима (понимание команд);
- [vision-v1](../../releases/tag/vision-v1) — модели для фото: лица, люди, что на фото, узнавание знакомых,
  подробное описание фото.

## Модели умного режима (models-v1)

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

## Модели для фото (vision-v1)

| Файл | Что делает | Источник | Лицензия |
|---|---|---|---|
| `face_detection_yunet_2023mar.onnx` | находит лица | [opencv/face_detection_yunet](https://huggingface.co/opencv/face_detection_yunet) (OpenCV Zoo) | MIT, Copyright (c) 2020 Shiqi Yu |
| `object_detection_yolox_2022nov.onnx` | находит людей | [opencv/object_detection_yolox](https://huggingface.co/opencv/object_detection_yolox) (OpenCV Zoo, YOLOX — Megvii) | Apache 2.0 |
| `siglip_vision_quantized.onnx` | понимает, что на фото | [Xenova/siglip-base-patch16-224](https://huggingface.co/Xenova/siglip-base-patch16-224) (конверсия [google/siglip-base-patch16-224](https://huggingface.co/google/siglip-base-patch16-224)) | Apache 2.0 |
| `face_recognition_sface_2021dec.onnx` | узнаёт знакомых | [opencv/face_recognition_sface](https://huggingface.co/opencv/face_recognition_sface) (OpenCV Zoo) | Apache 2.0 |
| `Qwen3VL-4B-Instruct-Q4_K_M.gguf` + `mmproj-Qwen3VL-4B-Instruct-Q8_0.gguf` | подробно описывает фото | [Qwen/Qwen3-VL-4B-Instruct-GGUF](https://huggingface.co/Qwen/Qwen3-VL-4B-Instruct-GGUF) | Apache 2.0 |

Файлы не изменялись. Текст лицензии лежит в релизе рядом с каждой моделью (`имя-модели.LICENSE.txt`).

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
