---
layout: splash
permalink: /
hidden: true
header:
  overlay_color: "#3F91C5"
  title: "MatchZoo"
  # overlay_image: /assets/images/mm-home-page-feature.jpg
  actions:
    - label: "<i class='fas fa-download'></i> Install MatchZoo"
      url: "https://github.com/NTMC-Community/MatchZoo"
    - label: "<i class='fas fa-download'></i> Install MatchZoo-py"
      url: "https://github.com/NTMC-Community/MatchZoo-py"
excerpt: >
  Facilitating the design, comparison and sharing of deep text matching models.

community:
  - image_path: /assets/images/matchzoo-feature.png
    alt: "customizable"
    title: "Get started"
    excerpt: "Get started"
    url: "/tutorials/installation/"
    btn_class: "btn--primary"
    btn_label: "Learn more"
  - image_path: /assets/images/matchzoo-feature.png
    alt: "fully responsive"
    title: "Documentation"
    excerpt: "Documentation."
    url: "https://matchzoo.readthedocs.io/en/master/"
    btn_class: "btn--primary"
    btn_label: "Learn more"
  - image_path: /assets/images/matchzoo-feature.png
    alt: "100% free"
    title: "Resources"
    excerpt: "Resources"
    url: "/resources/community-question-answering/"
    btn_class: "btn--primary"
    btn_label: "Learn more"

features:
  - title: "Production Ready"
    excerpt: "Transition seamlessly between eager and graph modes with TorchScript, and accelerate the path to production with TorchServe."
  - title: "SOTA Models"
    excerpt: "Scalable distributed training and performance optimization in research and production is enabled by the torch.distributed backend."
  - title: "Text Matching Progress"
    excerpt: "A rich ecosystem of tools and libraries extends PyTorch and supports development in computer vision, NLP and more."

brand:
  - image_path: /assets/images/brand/ict.png
  - image_path: /assets/images/brand/tsinghua.png
  - image_path: /assets/images/brand/cloudbrain.png

---

<h2>KEY FEATURES & CAPABILITIES</h2>
{% include feature_row id="features"%}

## COMMUNITY
{% include feature_row id="community"%}

## COMPANIES & UNIVERSITIES USING MATCHZOO
{% include feature_row id="brand"%}
