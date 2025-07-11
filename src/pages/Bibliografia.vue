<template>
  <div class="curso-main-container referencias">
    <BannerInterno
      icono="fas fa-book"
      titulo="Referencias bibliográficas"
    ></BannerInterno>
    <div class="container tarjeta tarjeta--blanca p-4 p-md-5 mb-5">
      <div v-for="ref in orderedData" :key="ref.link" class="referencias__item">
        <span v-html="ref.referencia"></span
        ><a v-if="ref.link" class="ms-1" :href="ref.link" target="_blank"
          ><span v-html="ref.link"></span
          ><i class="ms-1 fas fa-external-link-alt"></i
        ></a>
        <hr class="my-3" />
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: 'Referencias',
  data: () => ({
    referencias: [
      {
        referencia:
          'AWS. (n.d.). ¿Qué es el aprendizaje automático? Recuperado de',
        link: 'https://aws.amazon.com/es/what-is/machine-learning/',
      },
      {
        referencia:
          'Barbara, J. (2023). Practical C++ Backend Programming: Crafting Databases, APIs, and Web Servers for High-Performance Backend. GitforGits.',
        link: '',
      },
      {
        referencia:
          'Brandao, M., Iago, & da Costa, C. (2022). Fault diagnosis of rotary machines using machine learning. Eletrônica de Potência, 27(03), 1–8.',
        link: 'http://dx.doi.org/10.18618/rep.2022.3.0013',
      },
      {
        referencia:
          'García, S., Luengo, J., & Herrera, F. (2021). Data Preprocessing in Data Mining and Machine learning: New Frameworks, Algorithms and Applications. Springer.',
        link: '',
      },
      {
        referencia:
          'Géron, A. (2022). Hands-on machine learning with Scikit-Learn, Keras, and TensorFlow: Concepts, tools, and techniques to build intelligent systems (3rd ed.). O&#39;Reilly Media.',
        link: '',
      },
      {
        referencia:
          'Janiesch, C., Zschech, P., & Heinrich, K. (2021). Machine learning and deep learning. Electronic Markets, 31(3), 685–695.',
        link: 'https://doi.org/10.1007/s12525-021-00475-2',
      },
      {
        referencia:
          'Knaflic, C. N. (2023). Storytelling with Data: A Data Visualization Guide for Business Professionals (2nd ed.). Wiley.',
        link: '',
      },
      {
        referencia:
          'Molnar, C. (2022). Interpretable Machine learning: A Guide for Making Black Box Models Explainable (2nd ed.). Leanpub.',
        link: 'https://christophm.github.io/interpretable-ml-book/',
      },
      {
        referencia:
          'Moreno-Jiménez, J. M., & Escobar Urmeneta, M. T. (2020). El proceso analítico jerárquico (AHP). Fundamentos, metodología y aplicaciones. RECTA Monográficos, 1, 21-53.',
        link: '',
      },
      {
        referencia:
          'Mudunuru, M. K., Ahmmed, B., Rau, E., Vesselinov, V. V., & Karra, S. (2023). Machine Learning for Geothermal Resource Exploration in the Tularosa Basin, New Mexico. Energies, 16(7), 3098.',
        link: 'https://doi.org/10.3390/en16073098',
      },
      {
        referencia:
          'Nelli, F. (2023). Python Data Analytics: With Pandas, NumPy, and Matplotlib (3rd ed.). Apress.',
        link: '',
      },
      {
        referencia:
          'Polanía Arias, L. A. (2021). Evaluación de modelos de Machine learning para Sistemas de Detección de Intrusos en Redes IoT. Universidad de los Andes. Recuperado de ',
        link:
          'https://repositorio.uniandes.edu.co/server/api/core/bitstreams/c6f1ea83-58d7-4eb6-a1ba-c3457306c054/content',
      },
      {
        referencia:
          'Raschka, S., Patterson, J., & Nolet, C. (2022). Machine learning with PyTorch and Scikit-Learn: Develop machine learning and deep learning models with Python. Packt Publishing.',
        link: '',
      },
      {
        referencia:
          'Rudin, C., Chen, C., Chen, Z., Huang, H., Semenova, L., & Zhong, C. (2022). Interpretable machine learning: Fundamental principles and 10 grand challenges. Statistics Surveys, 16, 1–85.',
        link: 'https://doi.org/10.1214/21-SS133',
      },
      {
        referencia:
          'Sarker, I. H. (2021, May 1). Machine learning: Algorithms, Real-World Applications and Research Directions. SN Computer Science. Springer.',
        link: 'https://doi.org/10.1007/s42979-021-00592-x',
      },
      {
        referencia:
          'Topuz, K., Bajaj, A., & Abdulrashid, I. (2023). Interpretable Machine learning. In Proceedings of the Annual Hawaii International Conference on System Sciences (Vol. 2023-January, pp. 1236–1237). IEEE Computer Society.',
        link: 'https://doi.org/10.1201/9780367816377-16',
      },
    ],
  }),
  computed: {
    orderedData() {
      return [...this.referencias].sort((a, b) => {
        const afl = this.quitarAcentos(a.referencia.split(' ')[0].toLowerCase())
        const bfl = this.quitarAcentos(b.referencia.split(' ')[0].toLowerCase())
        if (afl < bfl) return -1
        if (afl > bfl) return 1
        return 0
      })
    },
  },
  methods: {
    quitarAcentos(str) {
      return str.normalize('NFD').replace(/[\u0300-\u036f]/g, '')
    },
  },
}
</script>

<style lang="sass">
.referencias
  &__item
    &:last-child
      hr
        display: none
    a
      color: $blue
      text-decoration: underline
      overflow-wrap: break-word
</style>
