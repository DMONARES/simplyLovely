<script setup>
const heroSection = {
	title: 'Делаем маркетинг лучше',
	subtitle: 'За счет общей стратегии и синергии для брендинга и performance.',
	img: '/img/hero/hero-title-image.png',
	video: null
};

const casesSection = {
	header: {
		title: 'Кейсы',
		subtitle: 'Где мы реализуем подход брендформанса, который включает синергию и дает крутые результаты в долгосрочной перспективе.',
	},
	cases: [
		{
			title: 'Новый бренд и сайт для дистрибьютора звукового оборудования Cromi',
			img: '/img/main-cases/1.jpg',
			categories: ['Стратегия', 'Продвиженеие', 'Сайт']
		},
		{
			title: 'Вывели международного интегратора IT-сервисов Orange в digital в России',
			img: '/img/main-cases/2.jpg',
			categories: ['Стратегия', 'Продвиженеие', 'Сайт']
		},
		{
			title: 'Обновили образ бренда и привлекли новых покупателей для дистрибьютера «Во!Молоко»',
			img: '/img/main-cases/3.jpg',
			blackText: true,
			categories: ['Стратегия', 'Продвиженеие', 'Сайт']
		},
		{
			title: 'Бренд-стратегия для производителя резиновых сапогов KAURY',
			img: '/img/main-cases/4.jpg',
			categories: ['Стратегия', 'Продвиженеие', 'Сайт']
		},
		{
			title: 'Фирменный стиль и сайт для международной транферной компании Riderra',
			img: '/img/main-cases/5.jpg',
			categories: ['Стратегия', 'Продвиженеие', 'Сайт']
		},
		{
			title: 'Контент-маркетинг, сайт и видео для бренда украшений Darkrain',
			img: '/img/main-cases/6.jpg',
			foreign: true,
			categories: ['Стратегия', 'Продвиженеие', 'Сайт']
		},
		{
			title: 'Привлекли 10 000 подписчиков в Instagram для бренда Toofli',
			img: '/img/main-cases/7.jpg',
			categories: ['Стратегия', 'Продвиженеие', 'Сайт']
		},
	],
	lastCardText: 'Смотреть больше кейсов'
};

const blogSlider = {
	header: {
		title: 'Блог',
		subtitle: 'Делимся опытом в стратегии и инструментах маркетинга, а также рассказываем, как устроена наша внутренняя кухня.',
	},
	cases: [
		{
			title: 'Как сделать бренд, который полюбят клиенты?',
			img: '/img/main-blog/1.png',
		},
		{
			title: 'Почему digital-агентства отправляют коммерческие предложения, а не прайс-лист',
			subtitle: 'Как время влияет на качество услуг и результаты.',
			img: '/img/main-blog/2.png',
		},
		{
			title: 'Performance-маркетинг и брендинг: почему одно без другого — слив бюджета',
			img: '/img/main-blog/3.png',
		},
	],
	lastCardText: 'Больше материалов читайте в нашем блоге',
}

const servicesSlider = {
	header: {
		title: 'Услуги',
		subtitle: 'Создаем комплексный маркетинг на основе исследований, стратегии и брендформанса.',
	},
	cases: [
		{
			title: 'Комплексное продвижение',
			subtitle: 'Доносим преимущества бренда до аудитории и увеличиваем конверсию через различные инструменты.',
			img: '/img/main-services/1.png',
		},
		{
			title: 'Маркетинговая стратегия',
			subtitle: 'Долгосрочно развиваем бизнес через планы по улучшению продаж и продвижению',
			img: '/img/main-services/2.png',
		},
		{
			title: 'Фирменный стиль',
			subtitle: 'Разрабатываем логотип и элементы фирменного стиля, которые будут привлекать внимание и нравиться вашей аудитории.',
			img: '/img/main-services/3.png',
		},
		{
			title: 'Сайт',
			subtitle: 'Создаем сайты, помогающие раскрыть бренд, влюбить в себя клиентов, увеличить продажи продуктов и услуг.',
			img: '/img/main-services/4.png',
		},
	],
	lastCardText: 'Больше услуг на сайте',
}
</script>

<template>
  <div>
    <HeroTitleBlock :data="heroSection"/>

    <Case
      :data="casesSection"
      layout="grid"
      header-variant="column"
    />

    <Case
      :data="blogSlider"
      layout="slider"
      header-variant="row"
    />

    <Case
      :data="servicesSlider"
      layout="slider"
      header-variant="row"
    />
  </div>
</template>

<style lang="scss"></style>
