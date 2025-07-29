<template>
  <div class="curso-main-container complementario">
    <BannerInterno
      icono="far fa-folder-open"
      titulo="Material complementario"
    ></BannerInterno>
    <div class="container tarjeta tarjeta--blanca p-4 p-md-5 mb-5">
      <div class="table-responsive">
        <table>
          <thead>
            <tr>
              <th colspan="3" scope="col">Tema</th>
              <th colspan="5" scope="col">Referencia APA del material</th>
              <th colspan="2" scope="col">Tipo</th>
              <th colspan="2" scope="col">Enlace</th>
            </tr>
          </thead>
          <tbody>
            <tr
              v-for="(item, index) in computedData"
              :key="'complementario-' + index"
            >
              <td
                class="text-start"
                colspan="3"
                scope="row"
                v-html="item.tema"
              ></td>
              <td
                class="text-start"
                colspan="5"
                scope="row"
                v-html="item.referencia"
              ></td>
              <td colspan="2" v-html="item.tipo"></td>
              <td colspan="2">
                <div class="complementario__enlaces">
                  <a
                    v-for="(link, linkIndex) of item.link"
                    :key="linkIndex"
                    class="complementario__btn"
                    :href="link"
                    target="_blank"
                    ><i class="fas fa-external-link-alt"></i
                  ></a>
                </div>
              </td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: 'MaterialComplementario',
  computed: {
    complementarioData() {
      return [
        {
          tema:
            '1. Introducción a la evaluación de modelos de <em>machine learning</em>',
          referencia:
            'Ecosistema de Recursos Educativos Digitales SENA. (2023, septiembre 15). Introducción al <em>Machine learning</em>.',
          tipo: 'Video',
          link: 'https://www.youtube.com/watch?v=xwjQmGJ3q0I',
        },
        {
          tema:
            '1. Introducción a la evaluación de modelos de <em>machine learning</em>',
          referencia:
            'Ecosistema de Recursos Educativos Digitales SENA. (2020, 13 septiembre). ¿Qué es <em>Machine learning</em>?',
          tipo: 'Video',
          link: 'https://www.youtube.com/watch?v=J9w6KquPKbE',
        },
        {
          tema:
            '2. Técnicas de ensamblado de modelos de inteligencia artificial',
          referencia:
            'Ecosistema de Recursos Educativos Digitales SENA. (2023, agosto 18). Aprendizaje no supervisado K-means.',
          tipo: 'Video',
          link: 'https://www.youtube.com/watch?v=yVIf4MtNg_c',
        },
        {
          tema:
            '2. Técnicas de ensamblado de modelos de inteligencia artificial',
          referencia:
            'Ecosistema de Recursos Educativos Digitales SENA. (2023, marzo 27). Algoritmos usados en aprendizaje no supervisado.',
          tipo: 'Video',
          link: 'https://www.youtube.com/watch?v=iZ6soC3Nx9M',
        },
        {
          tema: '3. Métricas avanzadas de evaluación y ajuste de modelos',
          referencia:
            'Ecosistema de Recursos Educativos Digitales SENA. (2023, octubre 10). <em>Machine learning</em> con Python.',
          tipo: 'Video',
          link: 'https://www.youtube.com/watch?v=noMy4-zjR9Q',
        },
        {
          tema: '3. Métricas avanzadas de evaluación y ajuste de modelos',
          referencia:
            'Ecosistema de Recursos Educativos Digitales SENA. (2023, marzo 17). Optimización de datos previo a la creación de modelos de <em>machine learning</em>.',
          tipo: 'Video',
          link: 'https://www.youtube.com/watch?v=tkeCwwPOVIU',
        },
        {
          tema: '4. Comunicación y documentación de resultados',
          referencia:
            'Ecosistema de Recursos Educativos Digitales SENA. (2022, 26 diciembre). Introducción a la visualización de datos.',
          tipo: 'Video',
          link: 'https://www.youtube.com/watch?v=-7nn2bm07Dw',
        },
      ]
    },
    computedData() {
      const data = this.complementarioData
      return data.map(item => {
        let nuevoLink = []
        if (item.link) {
          if (typeof item.link === 'string') {
            nuevoLink.push(item.link)
          } else {
            nuevoLink = item.link
          }
        } else if (item.descarga) {
          if (typeof item.descarga === 'string') {
            nuevoLink.push(this.obtenerLink(item.descarga))
          } else {
            item.descarga.forEach(link => {
              nuevoLink.push(this.obtenerLink(link))
            })
          }
        }
        return {
          ...item,
          link: nuevoLink,
        }
      })
    },
  },
}
</script>

<style lang="sass">
.complementario
  &__enlaces
    display: flex
    justify-content: center
    flex-wrap: wrap
    a
      margin: 0 5px
  &__btn
    font-size: 1.5em
    line-height: 1em
table
  width: calc(100% - 1px)
  min-width: 800px
  thead
    background-color: $color-sistema-e
    th
      border-color: $color-sistema-e
  th, td
    padding: 25px 20px
    text-align: center
</style>
