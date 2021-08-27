## Welcome to GitHub Page Proyecto_Vision
#!/usr/bin/env python3
import json
from urllib.request import urlopen, Request

inputs = {
  "image": <base 64 image>,
  "threshold": <number from 0.01 to 1>
}

req = Request(
  "https://proyecto-vision.hosted-models.runwayml.cloud/v1/query",
  method="POST",
  headers={
    "Accept": "application/json",
    "Content-Type": "application/json",
  },
  data=json.dumps(inputs).encode("utf8")
)

with urlopen(req) as url:
  output = json.loads(url.read().decode("utf8"))

bounding_boxes = output["bounding_boxes"]
categories = output["categories"]
scores = output["scores"]
# use the outputs in your project

#!/usr/bin/env python3
import json
from urllib.request import urlopen, Request

req = Request(
  "https://proyecto-vision.hosted-models.runwayml.cloud/v1/info",
  method="GET",
  headers={
    "Accept": "application/json",
    "Content-Type": "application/json",
  },
)

with urlopen(req) as url:
  info = json.loads(url.read().decode("utf8"))

name = info["name"]
description = info["description"]
inputs = info["inputs"]
outputs = info["outputs"]
# use the info in your project

#!/usr/bin/env python3
import json
from urllib.request import urlopen, Request

req = Request(
  "https://proyecto-vision.hosted-models.runwayml.cloud/v1/",
  method="GET",
  headers={
    "Accept": "application/json",
    "Content-Type": "application/json",
  },
)

with urlopen(req) as url:
  metadata = json.loads(url.read().decode("utf8"))
  
status = metadata["status"]
query_route = metadata["queryRoute"]
# use the metadata + status in your project
