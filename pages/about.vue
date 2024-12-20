<template>
  <div v-if="isLoading" class="flex justify-center items-center h-screen">
    Loading...
  </div>
  <div v-else class="leading-tight mb-24">
    <GeneralizedHeader
      :left-items="headerLinks"
      :right-items="[{ label: 'Взяти участь', color: 'black', to: '/' }]"
      class="z-20"
      logo-src="/restart-logo-icon.svg"
      logo-alt="Restart Agency Logo"
      logo-link="https://www.restartfuture.org/"
    />

    <AboutHero
      image="/hurtoma-river-01.jpg"
      title="Гуртомá"
      :buttons="heroButtons"
    >
      <p>
        Платформа від команди дослідників та містопланувальників Restart, яка
        спрощує комунікацію між містянами та урбаністами. Мета — покращувати
        міста і спільноти разом.
      </p>
      <p>
        Завдяки доступній онлайн мапі, платформа збирає зворотний зв'язок щодо
        улюблених локації та місць, які потребують покращень. А також враховує
        побажання уряду, громадських організацій та інших стейкхолдерів.
      </p>
    </AboutHero>

    <UDivider class="mt-24 mb-8" />

    <AboutFeatureGrid :features="features" />

    <UDivider class="mt-24 mb-8" />

    <AboutSection
      title="Візія"
      image="/hurtoma-river-02.jpg"
      imageClass="w-7/12 rounded-md"
    >
      <p>
        Річка Тяжилівка, оточена промисловими та військовими районами Вінниці,
        фактично ізольована від міста. Важкодоступність цієї території заважає
        мешканцям використовувати її потенціал на користь спільноті.
      </p>
      <p>
        Проєкт відновлення «Малі річки Вінниці», в межах якого платформа від
        Restart стала цифровим партнером, спрямований на відновлення зв'язку між
        річкою та міським простором. Ініціатива є частиною більшої стратегії
        Зеленого курсу Вінниці, яку міська рада оголосила в січні 2022 року.
        Мета — забезпечити сталий розвиток міста через екологічно орієнтовані
        проєкти та активне залучення інвестицій для покращення інфраструктури.
      </p>
      <p>
        Ще одним партнером виступає «Інститут розвитку міст», який вже
        реалізував кілька важливих проєктів для сталого розвитку Вінниці (один з
        яких — «Вінницький луг»).
      </p>
      <p>
        У випадку з річкою Тяжилівка як першим проєктом, платформа «Гуртомá»
        дозволить вінничанам самостійно обирати, де прокласти дорогу, створити
        зону для відпочинку або розчистити територію від зайвого сміття. Зокрема
        це актуально для жителів віддалених мікрорайонів, які можуть впливати на
        зміни в один клік.
      </p>
    </AboutSection>

    <UDivider class="mt-24 mb-8" />

    <AboutSection title="Наші партнери">
      <p>
        Програмне забезпечення у цифровій платформі розробила команда Карлоса
        Сандовала Оласкоага. Він є доцентом кафедри взаємодії людини з
        комп'ютером (human-computer interaction) та інклюзивного дизайну
        (inclusive design) в Школі архітектури Північно-Східного університету
        (School of Architecture at Northeastern University). А також
        асоційованим доцентом Коледжу комп'ютерних наук Хурі Північно-Східного
        університету (Khoury College of Computer Sciences at Northeastern
        University). Зокрема Карлос керує лабораторією масштабованої участі у
        дизайні (Scalable Design Participation Lab).
      </p>
      <p>
        у Північно-Східному університеті й спільно очолює локальну кодову
        лабораторію (Local Code Lab) в MIT. Його робота поєднує проєктування,
        обчислення, роботу з міськими даними та державними послугами. Це
        дозволяє широкому колу спільноти формувати власне цифрове середовище
        справедливо та цілісно за допомогою обчислювального інтелекту.
      </p>
    </AboutSection>

    <UDivider class="mt-24 mb-8" />

    <AboutFooter :logos="footerLogos" :links="footerLinks">
      <template #title> Drawing Participation<br />Гуртомá </template>
    </AboutFooter>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue'

const isLoading = ref(true)
const headerLinks = ref([
  { label: 'Drawing Participation', color: 'black', to: '/' },
  { label: 'Гуртомá', color: 'black', to: '/' },
])

const heroButtons = [
  { label: 'Взяти участь', to: '/' },
  { label: 'Подивитись результати', to: '/map/', secondary: true },
]

const features = [
  {
    title: 'Безпека',
    description:
      'Ми створили цифровий простір, де можна відверто ділитися думками й спогадами про місця, яких уникаєте. Це допоможе привернути увагу спільноти й запустити процес змін.',
  },
  {
    title: 'Приналежність',
    description:
      'Стежка до річки, квітучий сквер, культурний центр — позначайте улюблені місця та дізнавайтеся, які локації обирають інші містяни.',
  },
  {
    title: 'Середовище',
    description:
      'Завдяки згуртованості містян, онлайн мапа наочно відображає популярні локації та ділянки, які потребують відновлення для процвітання міста.',
  },
  {
    title: 'Екологія',
    description:
      'Платформа збирає й систе-матизує дані про рослини та тварин, характерних для місцевості. А також фіксує засмічені зони, які гальмують розвиток міста. Поділитися своїми враженнями — перший крок до покращень.',
  },
]

const footerLogos = [
  {
    url: 'https://www.northeastern.edu',
    src: '/neu-logo-text.svg',
    alt: 'Northeastern University Logo',
  },
  {
    url: 'https://www.restartfuture.org',
    src: '/restart-logo-text.svg',
    alt: 'Restart Agency Logo',
  },
  {
    url: 'https://www.facebook.com/SmallRiversVinnytsia',
    src: '/river-logo-text.svg',
    alt: 'Small Rivers Vinnytsia Project Logo',
  },
]

const footerLinks = [
  { to: '/', label: 'Карта' },
  { to: '/about/', label: 'Про проєкт' },
  { to: '/map/', label: 'Допомога' },
]

onMounted(() => {
  isLoading.value = false
})
</script>
