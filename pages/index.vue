<script setup>
const heroSection = {
	title: 'Делаем маркетинг лучше',
	subtitle: 'За счет общей стратегии и синергии для брендинга и performance.',
	img: '/img/hero/hero-title-image.png',
	video: null
};

const casesSection = {
	title: 'Кейсы',
	subtitle: 'Где мы реализуем подход брендформанса, который включает синергию и дает крутые результаты в долгосрочной перспективе.',
	cases: [
		{
			title: 'Новый бренд и сайт для дистрибьютора звукового оборудования Cromi',
			img: '/img/cases/1.webp',
			categories: ['Стратегия', 'Продвиженеие', 'Сайт']
		},
		{
			title: 'Вывели международного интегратора IT-сервисов Orange в digital в России',
			img: '/img/cases/3.webp',
			categories: ['Стратегия', 'Продвиженеие', 'Сайт']
		},
		{
			title: 'Обновили образ бренда и привлекли новых покупателей для дистрибьютера «Во!Молоко»',
			img: '/img/cases/4.webp',
			categories: ['Стратегия', 'Продвиженеие', 'Сайт']
		},
		{
			title: 'Бренд-стратегия для производителя резиновых сапогов KAURY',
			img: '/img/cases/5.webp',
			categories: ['Стратегия', 'Продвиженеие', 'Сайт']
		},
		{
			title: 'Фирменный стиль и сайт для международной транферной компании Riderra',
			img: '/img/cases/6.webp',
			categories: ['Стратегия', 'Продвиженеие', 'Сайт']
		},
		{
			title: 'Контент-маркетинг, сайт и видео для бренда украшений Darkrain',
			img: '/img/cases/7.webp',
			categories: ['Стратегия', 'Продвиженеие', 'Сайт']
		},
		{
			title: 'Привлекли 10 000 подписчиков в Instagram для бренда Toofli',
			img: '/img/cases/8.webp',
			foreign: true,
			categories: ['Стратегия', 'Продвиженеие', 'Сайт']
		},
	]
};
</script>

<template>
	<div>
		<HeroTitleBlock :data="heroSection"/>
		<CasesList :data="casesSection"/>
	</div>
</template>

<style lang="scss"></style>
