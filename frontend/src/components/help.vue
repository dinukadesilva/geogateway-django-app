<template>
  <div class="w-100 p-2 bg-light text-left">

    <h3>User Resources</h3>
    <!--
    <a href="https://archive.geo-gateway.org:3000/main.html" target="_blank"> <i>Visit the archived Geo-Gateway</i></a>
   -->
    <div class="tool-content">
      <a target="_blank"
         href="https://github.com/GeoGateway/GeoGatewayStaticResources/raw/master/documents/GeoGateway_User_Guide.pdf"><strong>User
        Guide (pdf)</strong></a>
      <br/>
      <a target="_blank" href="https://www.youtube.com/channel/UC0_bNEBxRWH2qBULDl6cB7Q/featured"><strong>Tutorial
        Videos</strong></a>
      <br/>
      <a target="_blank"
         href="https://github.com/GeoGateway/GeoGatewayStaticResources/raw/master/documents/GeoGateway_Exercises.pdf"><strong>Exercises
        (pdf)</strong></a>
      <br/><br/>
      <!--
         <strong>Recent Publications</strong>
         <div align="left" style="width:300px;">
         <b-list-group>
             <b-list-group-item v-for="item in papers" :key="item.year">
                 <a target="_blank" :href= "item.doiurl">{{ item.title }}</a>
              </b-list-group-item>
         </b-list-group>
         </div>
         <br/> -->
      <h3>More</h3>
      <a target="_blank" href="https://earthdata.nasa.gov/learn/articles/getting-started-with-sar"><strong>GSA 2020
        Workshop</strong></a>
      <br/><a target="_blank"
              href="https://cdn.earthdata.nasa.gov/conduit/upload/15244/GSA__2020_GeoGateway_updated_October_14.pdf"><strong>GSA
      2020 Workshop (slides)</strong></a>
      <br/><a target="_blank" href="https://youtu.be/Dz2JPgCpd-k"><strong>GSA 2020 Workshop (video)</strong></a>
      <br/>
      <a target="_blank"
         href="https://github.com/GeoGateway/GeoGatewayStaticResources/raw/master/documents/GeoGateway_SSA_Workshop.pdf"><strong>SSA
        2019 GeoGateway Workshop (slides)</strong></a>
    </div>
  </div>
</template>

<script>
export default {
  name: "help",
  data() {
    return {
      papers: [
        {
          title: 'Donnellan, A., Parker, J., Heflin, M. et al. Improving access to geodetic imaging crustal deformation data using GeoGateway. Earth Science Informatics, (2021).',
          doiurl: 'https://doi.org/10.1007/s12145-020-00561-7',
          year: 2021
        },
        {
          title: 'Heflin, M., Donnellan, A., Parker, J. et al. Automated Estimation and Tools to Extract Positions, Velocities, Breaks, and Seasonal Terms From Daily GNSS Measurements: Illuminating Nonlinear Salton Trough Deformation. Earth and Space Science, (2020).',
          doiurl: 'https://doi.org/10.1029/2019EA000644',
          year: 2020
        },
        {
          title: 'Parker, J., Bilham, R., Donnellan, A. et al. Buried Aseismic Slip and Off‐Fault Deformation on the Southernmost San Andreas Fault triggered by the 2010 El Mayor Cucapah Earthquake revealed by UAVSAR. Earth and Space Science, (2021).',
          doiurl: 'https://doi.org/10.1002/essoar.10506047.1',
          year: 2021
        },
      ],
    }
  },
}
</script>

<style scoped>

</style>

absl-py==0.12.0
ai-benchmark==0.1.2
appdirs==1.4.4
argon2-cffi==21.1.0
asgiref==3.4.1
astunparse==1.6.3
attrs==21.2.0
audioread==2.1.9
audiotsm==0.1.2
backcall==0.2.0
backports.ssl==0.0.9
beautifulsoup4==4.10.0
bleach==4.1.0
boto==2.49.0
bs4==0.0.1
cached-property==1.5.2
cachetools==4.2.4
causality==0.0.9
certifi==2021.5.30
cffi==1.14.6
chardet==4.0.0
charset-normalizer==2.0.6
clang==5.0
click==8.0.1
cloudpickle==2.0.0
colorama==0.4.4
commonmark==0.9.1
cryptography==35.0.0
css-inline==0.7.6
cupy==9.5.0
cycler==0.10.0
dask==2021.9.1
DateTime==4.3
debugpy==1.5.0
decorator==5.1.0
defusedxml==0.7.1
depinfo==1.7.0
dill==0.3.4
editdistance==0.5.3
elementpath==2.3.2
entrypoints==0.3
et-xmlfile==1.1.0
fastapi==0.68.2
fastobo==0.10.2.post1
fastrlock==0.6
flatbuffers==1.12
fsspec==2021.10.0
future==0.18.2
gast==0.4.0
google-api-core==2.0.1
google-auth==1.35.0
google-auth-oauthlib==0.4.6
google-cloud-core==2.0.0
google-cloud-storage==1.42.3
google-crc32c==1.2.0
google-pasta==0.2.0
google-resumable-media==2.0.3
googleapis-common-protos==1.53.0
graphviz==0.17
grpcio==1.41.0
guppy3==3.1.1
h11==0.12.0
h5py==3.7.0
horovod==0.22.1
html2text==2020.1.16
hyperspy==1.6.4
idna==3.2
imageio==2.9.0
importlib-metadata==4.8.1
imutils==0.5.4
iniconfig==1.1.1
ipykernel==6.4.1
ipyparallel==7.1.0
ipython==7.28.0
ipython-genutils==0.2.0
ipywidgets==7.6.5
isodate==0.6.0
jedi==0.18.0
Jinja2==3.0.2
joblib==1.0.1
jsonschema==4.0.1
jupyter==1.0.0
jupyter-client==7.0.6
jupyter-console==6.4.0
jupyter-core==4.8.1
jupyterlab-pygments==0.1.2
jupyterlab-widgets==1.0.2
keras==2.6.0
Keras-Applications==1.0.8
Keras-Preprocessing==1.1.2
kiwisolver==1.3.2
libroadrunner-experimental==2.0.10
librosa==0.9.1
llvmlite==0.37.0
locket==0.2.1
lxml==4.6.3
Markdown==3.3.4
markdown-it-py==1.1.0
Markov==0.4.0
MarkupSafe==2.0.1
mat73==0.59
matplotlib==3.4.3
matplotlib-inline==0.1.3
mistune==0.8.4
mpmath==1.2.1
mxnet-cu112==1.8.0.post0
natsort==7.1.1
nbclient==0.5.4
nbconvert==6.2.0
nbformat==5.1.3
nest-asyncio==1.5.1
networkx==2.6.3
nibabel==3.2.1
nltk==3.6.3
notebook==6.4.4
numba==0.54.0
numexpr==2.7.3
numpy==1.17.3
numpy-utils==0.1.6
oauthlib==3.1.1
opencv-contrib-python==4.5.3.56
opencv-python==4.5.3.56
openpyxl==3.0.9
opt-einsum==3.3.0
packaging==20.3
pandas==1.3.3
pandocfilters==1.5.0
parso==0.8.2
partd==1.2.0
patsy==0.5.2
pexpect==4.8.0
pickleshare==0.7.5
Pillow==8.3.2
Pint==0.17
platformdirs==2.4.0
pluggy==1.0.0
ply==3.10
pooch==1.6.0
prettytable==2.2.1
prometheus-client==0.11.0
promise==2.3
prompt-toolkit==3.0.20
pronto==2.4.3
protobuf==3.18.0
psutil==5.8.0
ptyprocess==0.7.0
py==1.10.0
py-cpuinfo==8.0.0
py2cytoscape==0.7.1
pyasn1==0.4.8
pyasn1-modules==0.2.8
pycparser==2.21
pydantic==1.8.2
pydnn==0.0.dev0
pydot==1.4.2
pydot-ng==2.0.0
pydotplus==2.0.2
Pygments==2.10.0
pymetadata==0.0.17
pyomexmeta==1.2.13
pyOpenSSL==21.0.0
pyparsing==2.2.1
pyrsistent==0.18.0
pytest==6.2.5
python-dateutil==2.8.2
python-igraph==0.9.6
python-libcombine==0.2.13
python-libsbml==5.19.0
python-libsbml-experimental==5.19.0
python-multipart==0.0.5
pytz==2021.3
PyWavelets==1.1.1
PyYAML==6.0
pyzmq==22.3.0
qtconsole==5.1.1
QtPy==1.11.2
regex==2021.9.30
requests==2.26.0
requests-file==1.5.1
requests-oauthlib==1.3.0
requests-toolbelt==0.9.1
resampy==0.2.2
rich==10.11.0
rsa==4.7.2
sasa==0.2.0
sbmlutils==0.5.7
scikit-image==0.18.3
scikit-learn==0.24.2
scipy==1.5.4
sds==2.0.1
Send2Trash==1.8.0
silence-tensorflow==1.1.1
six==1.15.0
SoundFile==0.10.3.post1
soupsieve==2.2.1
sparse==0.13.0
starlette==0.14.2
statsmodels==0.13.0
sympy==1.8
tabulate==0.8.9
tensorboard==2.6.0
tensorboard-data-server==0.6.1
tensorboard-plugin-wit==1.8.0
tensorflow==2.6.0
tensorflow-datasets==4.4.0
tensorflow-estimator==2.6.0
tensorflow-metadata==1.2.0
termcolor==1.1.0
terminado==0.12.1
testpath==0.5.0
texttable==1.6.4
Theano==1.0.5
threadpoolctl==3.0.0
tifffile==2021.8.30
toml==0.10.2
toolz==0.11.1
torch==1.9.1
torchaudio==0.10.2
torchvision==0.10.1+cu111
tornado==6.1
tqdm==4.64.0
traitlets==5.1.0
traits==6.2.0
typing-extensions==3.7.4.3
urllib3==1.26.7
uuid==1.30
uvicorn==0.15.0
vaderSentiment==3.3.2
wcwidth==0.2.5
webencodings==0.5.1
Werkzeug==2.0.1
widgetsnbextension==3.5.1
wrapt==1.12.1
xmlschema==1.8.0
xmltodict==0.12.0
zeep==4.1.0
zipp==3.6.0
zope.interface==5.4.0
