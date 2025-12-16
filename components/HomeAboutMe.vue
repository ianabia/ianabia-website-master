<template>
    <section class="about__section section">
        <div class="about__section__container container">
            <h2 class="small-title">
                {{ $t(about.title) }}
            </h2>
            <h3 class="large-title">
                {{ $t(about.subTitle) }}
            </h3>



            <div class="about__section__container__columns">

                <div class="about__section__container__columns__avatar">
                    <figure class="about__section__container__columns__avatar__image">

                        <NuxtImg v-if="colorMode.value == 'dark'" alt="Beatriz Nóbrega"
                            src="/images/anabia_avatar_v2.png" width="800px" height="800px" format="webp"
                            densities="x1 x2" quality="100" />

                        <NuxtImg v-if="colorMode.value == 'light'" alt="Beatriz Nóbrega"
                            src="/images/anabia_avatar_v3.png" width="800px" height="800px" format="webp"
                            densities="x1 x2" quality="100" />

                        <strong class="about__section__container__columns__avatar__image__areas logic">
                            <span>
                                <AppIcon class="smooth-move" IconName="ana-icon:" />
                                {{ locale == 'en' ? '' : '' }}
                            </span>
                        </strong>
                        <strong class="about__section__container__columns__avatar__image__areas creativity">
                            <span>
                                {{ locale == 'en' ? '' : '' }}
                                <AppIcon class="slide-top" IconName="ana-icon:" />
                            </span>
                        </strong>
                    </figure>


                </div>



                <div v-if="locale == 'en'" class="about__section__container__columns__text">
                    <p>
                        Hi, I’m Ana Beatriz—a seasoned <strong>Information Security professional transitioning into the Data field</strong>
                        from Brazil 🇧🇷. with With a solid background in technology and a strong focus on data analysis and organization, I am building a new
                        career path dedicated to transforming data into strategic insights.
                    </p>
                    <br />
                    <p>
                        I work with <strong>Design, Python (NumPy and Pandas), SQL, and Power BI</strong>, combining logical thinking,
                        analytical skills, and creativity to design efficient, well-structured, and visually impactful data-driven
                        solutions.
                    </p>
                    <br />
                    <p>
                        By blending technical expertise with a data-oriented mindset, I deliver solutions that support informed
                        decision-making and generate real business value.
                    </p>
                </div>
                <div v-else class="about__section__container__columns__text">
                    <p>
                        Olá, eu sou a Ana Beatriz profissional da <strong>área de Segurança da Informação em transição para o universo de Dados</strong>,
                        do Brasil 🇧🇷. Com uma base sólida em tecnologia e foco em análise e organização da informação, estou construindo uma nova
                        trajetória voltada à transformação de dados em insights estratégicos.
                    </p>
                    <br />
                    <p>
                        Atuo com <strong>Design, Python (NumPy e Pandas), SQL e Power BI</strong>, combinando raciocínio lógico,
                        visão analítica e criatividade para desenvolver soluções eficientes, bem estruturadas e visualmente impactantes.
                    </p>
                    <br />
                    <p>
                        Ao unir conhecimento técnico e uma mentalidade orientada a dados, entrego soluções que apoiam a tomada de decisões
                        e geram valor real para os negócios.
                    </p>
                </div>

            </div>

            <div class="about__section__container__stacks">
                <strong>
                    {{ $t(about.tools) }}
                </strong>
                <AppStackSkills :stacks="stackLogos" />
            </div>

            <div class="about__section__container__buttons">
                <AppButton :aria-label="$t(about.cta1)" class="primary" hasLink="/#contact">
                    {{ $t(about.cta1) }}
                </AppButton>
                <AppButton :aria-label="$t(about.cta2)" class="outline" target="_new" :hasLink="$t(about.cta2Link)">
                    {{ $t(about.cta2) }}
                    <AppIcon IconName="ana-icon:arrow-up-right" />
                </AppButton>
            </div>

        </div>
    </section>
</template>

<script setup>
import { ref, useI18n, reactive } from '#imports'

const colorMode = useColorMode()
const { locale } = useI18n()
const stackLogos = ref([
    {logo: 'devicon:figma', name: 'Figma'},
    // {logo: 'devicon:sketch', name: 'Sketch'},
    {logo: 'skill-icons:xd', name: 'Adobe Xd'},
    {logo: 'skill-icons:photoshop', name: 'Adobe Photoshop'},
    {logo: 'skill-icons:illustrator', name: 'Adobe Illustrator'},
    {logo: 'devicon:javascript', name: 'Javascript'},
    {logo: 'devicon:typescript', name: 'Typescript'},
    {logo: 'devicon:html5', name: 'HTML 5'},
    {logo: 'devicon:css3', name: 'CSS 3'},
    {logo: 'devicon:python', name: 'Python'},
    {logo: 'devicon:mysql', name: 'MySQL'},
    {logo: 'devicon:postgresql', name: 'PostgreSQL'},
    {logo: 'skill-icons:wordpress', name: 'Wordpress'},
    {logo: 'devicon:docker', name: 'Docker'},
    {logo: 'devicon:azure', name: 'Azure'},
    {logo: 'skill-icons:django', name: 'Django'},
    {logo: 'skill-icons:mongodb', name: 'MongoDB'},
    {logo: 'devicon:linux', name: 'Linux'},
    {logo: 'devicon:debian', name: 'Debian'},
    {logo: 'logos:visual-studio-code', name: 'Visual Studio Code'},
    {logo: 'devicon:github', name: 'GitHub'},
    {logo: 'devicon:gitlab', name: 'GitLab'}
    // {logo: 'logos:blender', name: 'Blender'},
])

const about = reactive({
    title: 'about.title',
    subTitle: 'about.subtitle',
    tools: 'about.tools',
    cta1: 'about.cta_1',
    cta2: 'about.cta_2',
    cta2Link: 'about.cta_2_link'
})
</script>

<style lang="scss" scoped>
.about__section{
    padding-block: 80px;
    &__container{
        max-width: 920px;
        display: grid;
        position: relative;
        .small-title, .large-title{
            text-align: center;
            max-width: 600px;
            margin: auto;
        }
        &__stacks{
            margin-block: 40px;
            font-family: $font_secondary;
            text-transform: uppercase;
            font-size: $size_16px;
            text-align: center;
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 40px;
            strong{
                font-weight: 300;

            }
        }
        &__columns{
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 20px;
            margin-block: 40px;
            @media(max-width: $br_tablet){
                grid-template-columns: 1fr;
            }
            &__avatar{
                margin-block: 20px;
                position: relative;
                display: grid;
                place-items: center;
                &__image{
                    border-radius: 20px;
                    background-color: var(--primary);
                    // background: var(--secondary_gradient);
                    // overflow: hidden;
                    aspect-ratio: 1;
                    position: relative;
                    display: grid;
                    place-items: center;
                    transition: $transition_default;
                    max-width: 300px;
                    // animation: pulse 2s ease infinite;
                    &__areas{
                        position: absolute;
                        display: grid;
                        place-items: center;
                        color: var(--text_color);
                        z-index: 2;
                        span{
                            display: flex;
                            gap: 4px;
                            flex-direction: column;
                            transition: $transition_default;
                            text-align: center;
                            font-family: $font_secondary;
                            text-transform: uppercase;
                            // font-weight: normal;
                        }
                        i{
                            font-size: 168px;
                        }
                        &.logic{
                            transform: translate( -132%, 40%);
                            
                        }
                        &.creativity{
                            transform: translate(90%, -40%);
                        }
                    }
                    

                    img{
                        position: relative;
                        display: block;
                        z-index: 2;
                        max-width: 300px;
                        max-height: 300px;
                        transition: $transition_default;
                        border-radius: 12px;
                        object-fit: cover;
                        min-width: 100%;
                        min-height: 100%;
                    }
                }

            }
            &__text{
                margin-block: 24px;
                position: relative;
                
                @media(max-width: $br_tablet){
                    text-align: center;
                }
                p{
                    font-size: $size_16px;
                    line-height: $size_32px;
                    margin: 0;
                    strong{
                        font-weight: 500;
                    }
                }
            }
        }
        &__buttons{
            display: flex;
            justify-content: center;
            gap: 20px;
            padding-block: 40px;
            flex-wrap: wrap;
            i{
                font-size: $size_24px;
            }
            @media(max-width: $br_mobile){
                justify-content: center;
                .button{
                    min-width: 90%;
                }
            }
        }
    }
}
</style>