{
  "nbformat": 4,
  "nbformat_minor": 0,
  "metadata": {
    "colab": {
      "name": "ContactosMexicanos10digitosVCF.ipynb",
      "provenance": [],
      "toc_visible": true,
      "mount_file_id": "1jBKqpP4-Oa_xVtDE1gyQDV8U3KJPY4QO",
      "authorship_tag": "ABX9TyNv7d6hNBaugnhf2mREqfEm",
      "include_colab_link": true
    },
    "kernelspec": {
      "name": "python3",
      "display_name": "Python 3"
    }
  },
  "cells": [
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "view-in-github",
        "colab_type": "text"
      },
      "source": [
        "<a href=\"https://colab.research.google.com/github/Joel301/vcf10digits/blob/main/ContactosMexicanos10digitosVCF.ipynb\" target=\"_parent\"><img src=\"https://colab.research.google.com/assets/colab-badge.svg\" alt=\"Open In Colab\"/></a>"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "mpN8fxPb9ugg"
      },
      "source": [
        "# Contactos Mexicanos 10 digitos version simple de escritorio\n",
        "---\n",
        "\n",
        "Con los cambios actuales de las formas de marcacion en Mexico multiples usuarios se ven retrasados en la forma de marcar. Es por eso que se hace este trabajo sencillo. Con la esperanza de eventualmente segirlo trabajando de forma abierta para solucionar una problematica sensilla.\n",
        "\n",
        "---\n",
        ">Para mas información: http://www.ift.org.mx/comunicacion-y-medios/comunicados-ift/es/partir-del-3-de-agosto-mexico-tendra-una-nueva-forma-de-marcacion-telefonica-comunicado-342019-16-de\n",
        "---\n",
        "Para generar data dummy se utilizo el generador proporcionado por @corysimmons https://github.com/corysimmons/vcf-generator"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "TU7W0lDXN_zh"
      },
      "source": [
        "## Se obtiene la data:"
      ]
    },
    {
      "cell_type": "code",
      "metadata": {
        "id": "pouKJgGTXkHZ"
      },
      "source": [
        "archivoOriginal = open('sample_data/dummy-contacts.vcf')\n",
        "contactos = [x for x in archivoOriginal.readlines()]"
      ],
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "5Me69Oc-H4zH"
      },
      "source": [
        "## Se modifica la data:"
      ]
    },
    {
      "cell_type": "code",
      "metadata": {
        "id": "iJx7agrBEodN"
      },
      "source": [
        "contactos = [x.replace('+521','') if x[:3]=='TEL' else x for x in contactos]\n",
        "contactos = [x.replace('+52 1','') if x[:3]=='TEL' else x for x in contactos]"
      ],
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "0SOe_-f0K_kM"
      },
      "source": [
        "## Se Guarda la informacion"
      ]
    },
    {
      "cell_type": "code",
      "metadata": {
        "id": "a1eGFh-1ILvE"
      },
      "source": [
        "with open('directorioResultado.vcf','w') as archivoFinal:\n",
        "  archivoFinal.writelines(contactos)"
      ],
      "execution_count": null,
      "outputs": []
    }
  ]
}
