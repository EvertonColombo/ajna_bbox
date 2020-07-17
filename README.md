# Ajna bouding boxes

Treinamento de modelo para detecção das bordas do contêiner em imagens de escaneamento

Para iniciar:

```
# git clone https://github.com/IvanBrasilico/ajna_bbox
# cd ajna_box
# python3 -m venv venv
# pip install -r requirements.txt
# hash -r
# ipython kernel install --user --name ajna_bbox ( para utilizar jupyter notebook, escolha kernel ajna_bbox)
```

Para rotular as imagens, instalar o labelImg. Pode ser instalado a partir dos fontes ou com pip.

Caso vá utilizar o exemplo com TF2 Object Detection API:
```
# git clone https://github.com/tensorflow/models.git
```
E seguir as instruções de instalação em:

[Object Detection API with TensorFlow 2](https://github.com/tensorflow/models/blob/master/research/object_detection/g3doc/tf2.md)

Ao seguir o tutotial acima, atenção para a versão do protoc a instalar. Deve ser instalada a versão 3 ou mais recente.
 
Baixar um modelo/checkpoint e configuração do site do Tensorflow e colocar no diretório bases/models/. Ex:
```
# wget http://download.tensorflow.org/models/object_detection/tf2/20200711/ssd_resnet50_v1_fpn_640x640_coco17_tpu-8.tar.gz
```

Copiar o modelo para o diretório bases/models/ssd_resnet50_v1_fpn_640x640_coco17_tpu-8
Utilizar o notebook generate_tf_records para gerar a base de treinamento para o tensorflow a partir das imagens rotuladas
em bases/baseline

Os caminhos do arquivo de configuração abaixo e da linha de comando devem ser modificados para a realidade local 

Editar o pipeline.config (num_classes e *_path) conforme exemplo em bases/models/ssd_resnet50_v1_fpn_640x640_coco17_tpu-8/pipepline.config

Rodar o comando para treinamento (mudando os caminhos para os caminhos locais):
```
#  python models/research/object_detection/model_main_tf2.py \
    --model_dir=/home/ivan/PycharmProjects/ajna_bbox/bases/models/ssd_resnet50_v1_fpn_640x640_coco17_tpu-8/ \
    --alsologtostderr \
    --pipeline_config_path=bases/models/ssd_resnet50_v1_fpn_640x640_coco17_tpu-8/pipeline.config \
    --use-tpu=true
```

Além do próprio guia da API do Tensorflow, os guias abaixo podem ser úteis:

[TensorFlow Object Detection API tutorial](https://tensorflow-object-detection-api-tutorial.readthedocs.io/)

[Deep Learning for Object Detection: A Comprehensive Review](https://towardsdatascience.com/deep-learning-for-object-detection-a-comprehensive-review-73930816d8d9)

[Machine Learning Mastery - train object detection keras](https://machinelearningmastery.com/how-to-train-an-object-detection-model-with-keras/)

[Object Detection on Custom Dataset](https://www.curiousily.com/posts/object-detection-on-custom-dataset-with-tensorflow-2-and-keras-using-python/)

[PyImageSearch: R-CNN object detection with Keras, TensorFlow, and Deep Learning](https://www.pyimagesearch.com/2020/07/13/r-cnn-object-detection-with-keras-tensorflow-and-deep-learning/)
