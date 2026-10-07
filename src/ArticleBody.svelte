<!-- 
@component
### ArticleBody component
This is a general workspace illustrating what an article body might look like if you use only the components included in this template.  
ArticleBody doesn't accept any props. All contents will need to be hand-placed by a designer directly inside this component.  
In this example, Grid and GridRow help establish the width of the article body's contents. 
Documentation included with those components and accessed by VSCode tooltip explains each component in greater detail.

#### State in this component
- innerWidth: int - pixel width of the viewport.
- isMobile: boolean - derived from innerWidth, true if less than 768 pixels
- isTablet: boolean - derived from innerWidth, true if between 768 pixels inclusive and 1160 pixels exclusive
- isDesktop: boolean - derived from innerWidth, true if greater than 1160 pixels inclusive

#### Using state in this component
You can use any of the three derived states to render different variants of a GridRow component reactively.
The following example uses a ternary to render an image edge-to-edge on mobile but inline otherwise.

#### Example
```svelte
  <GridRow
    variant={isMobile ? "fullBleed" : "inline"}
  >
    <Image
      src="https://arc.stimg.co/startribunemedia/4SPNT7DI36ANT2SOB5N5EJAIJU.jpg"
      alt="Descriptive alt text"
      caption="Caption tk tk tk"
    />
  </GridRow>
```
-->

<script>
  import { globalState } from './state.svelte.js';

  import Grid from './components/Grid/Grid.svelte';
  import GridRow from './components/Grid/_GridRow.svelte';
  import Subhead from './components/ArticleBody/_Subhead.svelte';
  import Paragraph from './components/ArticleBody/_Paragraph.svelte';
  import Dropcap from './components/ArticleBody/_Dropcap.svelte';
  import Image from './components/Image/Image.svelte';
  import Gallery from './components/Image/Gallery.svelte';
  import ScrollySection from './components/Scrolly/ScrollySection.svelte';
  import JWPlayer from './components/Video/JWPlayer.svelte';
  import Counter from './components/Counter/Counter.svelte';

  import Video from './components/Video/Video.svelte';

  import videos from './data/videos.json';

  let innerWidth = $state(0);
  let isMobile = $derived(innerWidth < 768);
  let isTablet = $derived(innerWidth >= 768 && innerWidth < 1160);
  let isDesktop = $derived(innerWidth >= 1160);
</script>

<svelte:window bind:innerWidth />
<Grid additionalClasses={'gap-y-5 px-4 md:px-6 min-[1080px]:px-0'}>
  <GridRow variant={'inline'} additionalClasses={'gap-y-5'}>
    <Paragraph>
      <Dropcap dropCapLines={3}>L</Dropcap>orem ipsum dolor sit amet consectetur
      adipisicing elit.
      <a href="https://www.startribune.com/" target="_blank" rel="noreferrer"
        >Debitis quas</a
      >, facilis itaque minus totam repudiandae magnam esse asperiores
      temporibus sed laborum nisi ut corporis ab officiis dolorum odio, porro
      eveniet. Quis quaerat tempore adipisci nostrum quia non.</Paragraph
    >
  </GridRow>

  <GridRow variant={'inline'} additionalClasses={'gap-y-5'}>
    <h2 class="font-[graphik-bold] text-2xl">Large photo blocks</h2>
    <h3 class="font-[graphik-semibold] text-lg">Large single image</h3>
  </GridRow>

  <GridRow variant={'fullBleed'} additionalClasses={''}>
    <!-- single image -->

    <div
      class="photo-block relative max-w-[1080px] col-span-full mx-auto max-[1079px]:px-[1.5rem] max-[767px]:px-[0] container-56945161 rt-Box col-span-8 md:col-span-6 md:col-start-2 lg:col-start-4"
    >
      <div class="pane">
        <img
          class="image aspect-[16/9] w-full object-cover object-center"
          src="https://arc.stimg.co/startribunemedia/IYHTBHX5YNDWVFLZKMZLTDOAV4.jpg?&w=800&ar=16:9&fit=crop&crop=bottom"
          alt=""
          loading="lazy"
          decoding="async"
        />
        <div
          class="caption font-utility-meta-reg-02 text-text-tertiary pt-2 px-4 md:px-0"
        >
          single photo cutline.
        </div>
      </div>
    </div>
  </GridRow>

  <GridRow variant={'inline'} additionalClasses={'gap-y-5'}>
    <Paragraph
      >Voluptate molestiae, perferendis iusto dolor officiis eaque cum quisquam
      quidem, doloremque dicta temporibus fuga ducimus voluptatum excepturi
      ratione laborum ab omnis quibusdam, accusamus vel eum culpa repellendus
      exercitationem. Fugit, consequatur!</Paragraph
    >
  </GridRow>
  <GridRow variant={'inline'} additionalClasses={'gap-y-5'}>
    <h3 class="font-[graphik-semibold] text-lg">Large 2-up layout</h3>
  </GridRow>

  <GridRow variant={'fullBleed'} additionalClasses={''}>
    <!-- 2up test -->

    <div
      class="photo-block relative max-w-[1080px] col-span-full mx-auto max-[1079px]:px-[1.5rem] max-[767px]:px-[0] container-34143651"
    >
      <div
        class="panes col-span-full grid grid-cols-12 gap-x-[.5rem] gap-y-4 md:gap-y-[.5rem]"
      >
        <div
          class="pane left-pane col-span-12 grid grid-cols-1 content-start md:col-span-6"
        >
          <img
            class="image aspect-[9/8] w-full object-cover object-center"
            src="https://arc.stimg.co/startribunemedia/VVT2BOQXYVFININIVGKSVMLBEE.jpg?&w=800&ar=9:8&fit=crop&crop=entropy"
            alt=""
            loading="lazy"
            decoding="async"
          />
          <div
            class="caption mobile-caption md:hidden font-utility-meta-reg-02 text-text-tertiary pt-2 px-4 md:px-0"
          >
            Left mobile caption
          </div>
        </div>
        <div
          class="pane right-pane col-span-12 grid grid-cols-1 content-start md:col-span-6"
        >
          <img
            class="image aspect-[9/8] w-full object-cover object-center"
            src="https://arc.stimg.co/startribunemedia/ETRAQPBUTJH3BMRDYRU3MWEOLU.jpg?&w=800&ar=9:8&fit=crop"
            alt=""
            loading="lazy"
            decoding="async"
          />
          <div
            class="caption mobile-caption md:hidden font-utility-meta-reg-02 text-text-tertiary pt-2 px-4 md:px-0"
          >
            Right mobile caption
          </div>
        </div>
      </div>
      <div
        class="caption desktop-caption col-span-full hidden md:block font-utility-meta-reg-02 text-text-tertiary pt-2"
      >
        2up gang caption for desktop.
      </div>
    </div>
  </GridRow>

  <GridRow variant={'inline'} additionalClasses={'gap-y-5'}>
    <Paragraph
      >Voluptate molestiae, perferendis iusto dolor officiis eaque cum quisquam
      quidem, doloremque dicta temporibus fuga ducimus voluptatum excepturi
      ratione laborum ab omnis quibusdam, accusamus vel eum culpa repellendus
      exercitationem. Fugit, consequatur!</Paragraph
    >
  </GridRow>
  <GridRow variant={'inline'} additionalClasses={'gap-y-5'}>
    <h3 class="font-[graphik-semibold] text-lg">Large 3-up layout</h3>
  </GridRow>

  <GridRow variant={'fullBleed'} additionalClasses={''}>
    <!-- 3up test -->

    <div
      class="photo-block relative max-w-[1080px] col-span-full mx-auto max-[1079px]:px-[1.5rem] max-[767px]:px-[0] container-23767192"
    >
      <div
        class="panes col-span-full grid grid-cols-12 gap-x-[.5rem] gap-y-4 md:gap-y-[.5rem]"
      >
        <div
          class="pane top-pane left-pane col-span-12 grid grid-cols-1 content-start md:col-span-6"
        >
          <img
            class="image top-image aspect-[16/16] w-full object-cover object-center"
            src="https://arc.stimg.co/startribunemedia/VEQFANTWDBHZZD3AWCQE3TMPEU.JPG?&w=800&ar=16:16&fit=crop&crop=left"
            alt=""
            loading="lazy"
            decoding="async"
          />
          <div
            class="caption mobile-caption md:hidden font-utility-meta-reg-02 text-text-tertiary pt-2 px-4 md:px-0"
          >
            Left mobile caption
          </div>
        </div>
        <div
          class="pane top-pane right-pane col-span-12 grid grid-cols-1 content-start md:col-span-6"
        >
          <img
            class="image top-image aspect-[16/16] w-full object-cover object-center"
            src="https://arc.stimg.co/startribunemedia/PVCAGYLU6RGVTKSV6BBVBMBEUI.JPG?&w=800&ar=16:16&fit=crop&crop=right"
            alt=""
            loading="lazy"
            decoding="async"
          />
          <div
            class="caption mobile-caption md:hidden font-utility-meta-reg-02 text-text-tertiary pt-2 px-4 md:px-0"
          >
            Right mobile caption
          </div>
        </div>
        <div
          class="pane bottom-pane col-span-12 grid grid-cols-1 content-start"
        >
          <img
            class="image bottom-image aspect-[16/9] w-full object-cover object-center"
            src="https://arc.stimg.co/startribunemedia/WPWXHD3ZXRCIHASIGUBZGYPEAE.JPG?&w=800&ar=16:9&fit=crop&crop=bottom"
            alt=""
            loading="lazy"
            decoding="async"
          />
          <div
            class="caption mobile-caption md:hidden font-utility-meta-reg-02 text-text-tertiary pt-2 px-4 md:px-0"
          >
            Bottom mobile caption
          </div>
        </div>
      </div>
      <div
        class="caption desktop-caption col-span-full hidden md:block font-utility-meta-reg-02 text-text-tertiary pt-2"
      >
        3up gang caption.
      </div>
    </div>
  </GridRow>

  <GridRow variant={'inline'} additionalClasses={'gap-y-5'}>
    <Paragraph
      >Voluptate molestiae, perferendis iusto dolor officiis eaque cum quisquam
      quidem, doloremque dicta temporibus fuga ducimus voluptatum excepturi
      ratione laborum ab omnis quibusdam, accusamus vel eum culpa repellendus
      exercitationem. Fugit, consequatur!</Paragraph
    >
  </GridRow>
  <GridRow variant={'inline'} additionalClasses={'gap-y-5'}>
    <h3 class="font-[graphik-semibold] text-lg">Large 4-up layout</h3>
  </GridRow>

  <GridRow variant={'fullBleed'} additionalClasses={''}>
    <!-- 4up -->

    <div
      class="photo-block relative max-w-[1080px] col-span-full mx-auto max-[1079px]:px-[1.5rem] max-[767px]:px-[0] container-27713791"
    >
      <div
        class="panes col-span-full grid grid-cols-12 gap-x-[.5rem] gap-y-4 md:gap-y-[.5rem]"
      >
        <div
          class="pane top-pane left-pane col-span-12 grid grid-cols-1 content-start md:col-span-6"
        >
          <img
            class="image top-image aspect-[16/12] w-full object-cover object-center"
            src="https://arc.stimg.co/startribunemedia/TSU46NVOFNO5YTLML34IQK3YQA.jpg?&w=800&ar=16:12&fit=crop&crop=top"
            alt=""
            loading="lazy"
            decoding="async"
          />
          <div
            class="caption mobile-caption md:hidden font-utility-meta-reg-02 text-text-tertiary pt-2 px-4 md:px-0"
          >
            top left mobile caption
          </div>
        </div>
        <div
          class="pane top-pane right-pane col-span-12 grid grid-cols-1 content-start md:col-span-6"
        >
          <img
            class="image top-image aspect-[16/12] w-full object-cover object-center"
            src="https://arc.stimg.co/startribunemedia/RUUTDFV6YY65XAOXGDQQSY7GCE.jpg?&w=800&ar=16:12&fit=crop&crop=entropy"
            alt=""
            loading="lazy"
            decoding="async"
          />
          <div
            class="caption mobile-caption md:hidden font-utility-meta-reg-02 text-text-tertiary pt-2 px-4 md:px-0"
          >
            top right mobile caption
          </div>
        </div>
        <div
          class="pane bottom-pane left-pane col-span-12 grid grid-cols-1 content-start md:col-span-6"
        >
          <img
            class="image bottom-image aspect-[16/12] w-full object-cover object-center"
            src="https://arc.stimg.co/startribunemedia/ANX6SDGLAE7WWGGYXW3GI2BI2Y.jpg?&w=800&ar=16:12&fit=crop&crop=entropy"
            alt=""
            loading="lazy"
            decoding="async"
          />
          <div
            class="caption mobile-caption md:hidden font-utility-meta-reg-02 text-text-tertiary pt-2 px-4 md:px-0"
          >
            bottom left mobile caption
          </div>
        </div>
        <div
          class="pane bottom-pane right-pane col-span-12 grid grid-cols-1 content-start md:col-span-6"
        >
          <img
            class="image bottom-image aspect-[16/12] w-full object-cover object-center"
            src="https://arc.stimg.co/startribunemedia/Y4IB6D6CRJQXM3XLQRPJZFHU4I.jpg?&w=800&ar=16:12&fit=crop&crop=entropy"
            alt=""
            loading="lazy"
            decoding="async"
          />
          <div
            class="caption mobile-caption md:hidden font-utility-meta-reg-02 text-text-tertiary pt-2 px-4 md:px-0"
          >
            bottom right mobile caption
          </div>
        </div>
      </div>
      <div
        class="caption desktop-caption col-span-full hidden md:block font-utility-meta-reg-02 text-text-tertiary pt-2"
      >
        4up gang caption for desktop.
      </div>
    </div>
  </GridRow>

  <GridRow variant={'inline'} additionalClasses={'gap-y-5'}>
    <h2 class="font-[graphik-bold] text-2xl">Medium photo blocks</h2>
    <h3 class="font-[graphik-semibold] text-lg">Medium single image</h3>
  </GridRow>

  <GridRow variant={'fullBleed'} additionalClasses={''}>
    <!-- single image -->

    <div
      class="photo-block relative max-w-[768px] min-[1079px]:max-w-[920px] col-span-full mx-auto px-[0] container-76603889 rt-Box col-span-8 md:col-span-6 md:col-start-2 lg:col-start-4"
    >
      <div class="pane">
        <img
          class="image aspect-[16/9] w-full object-cover object-center"
          src="https://arc.stimg.co/startribunemedia/IYHTBHX5YNDWVFLZKMZLTDOAV4.jpg?&w=800&ar=16:9&fit=crop&crop=bottom"
          alt=""
          loading="lazy"
          decoding="async"
        />
        <div
          class="caption font-utility-meta-reg-02 text-text-tertiary pt-2 px-4 md:px-0"
        >
          single photo cutline.
        </div>
      </div>
    </div>
  </GridRow>

  <GridRow variant={'inline'} additionalClasses={'gap-y-5'}>
    <Paragraph
      >Voluptate molestiae, perferendis iusto dolor officiis eaque cum quisquam
      quidem, doloremque dicta temporibus fuga ducimus voluptatum excepturi
      ratione laborum ab omnis quibusdam, accusamus vel eum culpa repellendus
      exercitationem. Fugit, consequatur!</Paragraph
    >
  </GridRow>
  <GridRow variant={'inline'} additionalClasses={'gap-y-5'}>
    <h3 class="font-[graphik-semibold] text-lg">Medium 2-up layout</h3>
  </GridRow>

  <GridRow variant={'fullBleed'} additionalClasses={''}>
    <!-- 2up test -->

    <div
      class="photo-block relative max-w-[768px] min-[1079px]:max-w-[920px] col-span-full mx-auto px-[0] container-58640349"
    >
      <div
        class="panes col-span-full grid grid-cols-12 gap-x-[.5rem] gap-y-4 md:gap-y-[.5rem]"
      >
        <div
          class="pane left-pane col-span-12 grid grid-cols-1 content-start md:col-span-6"
        >
          <img
            class="image aspect-[9/8] w-full object-cover object-center"
            src="https://arc.stimg.co/startribunemedia/VVT2BOQXYVFININIVGKSVMLBEE.jpg?&w=800&ar=9:8&fit=crop&crop=entropy"
            alt=""
            loading="lazy"
            decoding="async"
          />
          <div
            class="caption mobile-caption md:hidden font-utility-meta-reg-02 text-text-tertiary pt-2 px-4 md:px-0"
          >
            Left mobile caption
          </div>
        </div>
        <div
          class="pane right-pane col-span-12 grid grid-cols-1 content-start md:col-span-6"
        >
          <img
            class="image aspect-[9/8] w-full object-cover object-center"
            src="https://arc.stimg.co/startribunemedia/ETRAQPBUTJH3BMRDYRU3MWEOLU.jpg?&w=800&ar=9:8&fit=crop"
            alt=""
            loading="lazy"
            decoding="async"
          />
          <div
            class="caption mobile-caption md:hidden font-utility-meta-reg-02 text-text-tertiary pt-2 px-4 md:px-0"
          >
            Right mobile caption
          </div>
        </div>
      </div>
      <div
        class="caption desktop-caption col-span-full hidden md:block font-utility-meta-reg-02 text-text-tertiary pt-2"
      >
        2up gang caption for desktop.
      </div>
    </div>
  </GridRow>

  <GridRow variant={'inline'} additionalClasses={'gap-y-5'}>
    <Paragraph
      >Voluptate molestiae, perferendis iusto dolor officiis eaque cum quisquam
      quidem, doloremque dicta temporibus fuga ducimus voluptatum excepturi
      ratione laborum ab omnis quibusdam, accusamus vel eum culpa repellendus
      exercitationem. Fugit, consequatur!</Paragraph
    >
  </GridRow>
  <GridRow variant={'inline'} additionalClasses={'gap-y-5'}>
    <h3 class="font-[graphik-semibold] text-lg">Medium 3-up layout</h3>
  </GridRow>

  <GridRow variant={'fullBleed'} additionalClasses={''}>
    <!-- 3up test -->

    <div
      class="photo-block relative max-w-[768px] min-[1079px]:max-w-[920px] col-span-full mx-auto px-[0] container-29340045"
    >
      <div
        class="panes col-span-full grid grid-cols-12 gap-x-[.5rem] gap-y-4 md:gap-y-[.5rem]"
      >
        <div
          class="pane top-pane left-pane col-span-12 grid grid-cols-1 content-start md:col-span-6"
        >
          <img
            class="image top-image aspect-[16/16] w-full object-cover object-center"
            src="https://arc.stimg.co/startribunemedia/VEQFANTWDBHZZD3AWCQE3TMPEU.JPG?&w=800&ar=16:16&fit=crop&crop=left"
            alt=""
            loading="lazy"
            decoding="async"
          />
          <div
            class="caption mobile-caption md:hidden font-utility-meta-reg-02 text-text-tertiary pt-2 px-4 md:px-0"
          >
            Left mobile caption
          </div>
        </div>
        <div
          class="pane top-pane right-pane col-span-12 grid grid-cols-1 content-start md:col-span-6"
        >
          <img
            class="image top-image aspect-[16/16] w-full object-cover object-center"
            src="https://arc.stimg.co/startribunemedia/PVCAGYLU6RGVTKSV6BBVBMBEUI.JPG?&w=800&ar=16:16&fit=crop&crop=right"
            alt=""
            loading="lazy"
            decoding="async"
          />
          <div
            class="caption mobile-caption md:hidden font-utility-meta-reg-02 text-text-tertiary pt-2 px-4 md:px-0"
          >
            Right mobile caption
          </div>
        </div>
        <div
          class="pane bottom-pane col-span-12 grid grid-cols-1 content-start"
        >
          <img
            class="image bottom-image aspect-[16/9] w-full object-cover object-center"
            src="https://arc.stimg.co/startribunemedia/WPWXHD3ZXRCIHASIGUBZGYPEAE.JPG?&w=800&ar=16:9&fit=crop&crop=bottom"
            alt=""
            loading="lazy"
            decoding="async"
          />
          <div
            class="caption mobile-caption md:hidden font-utility-meta-reg-02 text-text-tertiary pt-2 px-4 md:px-0"
          >
            Bottom mobile caption
          </div>
        </div>
      </div>
      <div
        class="caption desktop-caption col-span-full hidden md:block font-utility-meta-reg-02 text-text-tertiary pt-2"
      >
        3up gang caption.
      </div>
    </div>
  </GridRow>

  <GridRow variant={'inline'} additionalClasses={'gap-y-5'}>
    <Paragraph
      >Voluptate molestiae, perferendis iusto dolor officiis eaque cum quisquam
      quidem, doloremque dicta temporibus fuga ducimus voluptatum excepturi
      ratione laborum ab omnis quibusdam, accusamus vel eum culpa repellendus
      exercitationem. Fugit, consequatur!</Paragraph
    >
  </GridRow>
  <GridRow variant={'inline'} additionalClasses={'gap-y-5'}>
    <h3 class="font-[graphik-semibold] text-lg">Medium 4-up layout</h3>
  </GridRow>

  <GridRow variant={'fullBleed'} additionalClasses={''}>
    <!-- 4up -->

    <div
      class="photo-block relative max-w-[768px] min-[1079px]:max-w-[920px] col-span-full mx-auto px-[0] container-15941360"
    >
      <div
        class="panes col-span-full grid grid-cols-12 gap-x-[.5rem] gap-y-4 md:gap-y-[.5rem]"
      >
        <div
          class="pane top-pane left-pane col-span-12 grid grid-cols-1 content-start md:col-span-6"
        >
          <img
            class="image top-image aspect-[16/12] w-full object-cover object-center"
            src="https://arc.stimg.co/startribunemedia/TSU46NVOFNO5YTLML34IQK3YQA.jpg?&w=800&ar=16:12&fit=crop&crop=top"
            alt=""
            loading="lazy"
            decoding="async"
          />
          <div
            class="caption mobile-caption md:hidden font-utility-meta-reg-02 text-text-tertiary pt-2 px-4 md:px-0"
          >
            top left mobile caption
          </div>
        </div>
        <div
          class="pane top-pane right-pane col-span-12 grid grid-cols-1 content-start md:col-span-6"
        >
          <img
            class="image top-image aspect-[16/12] w-full object-cover object-center"
            src="https://arc.stimg.co/startribunemedia/RUUTDFV6YY65XAOXGDQQSY7GCE.jpg?&w=800&ar=16:12&fit=crop&crop=entropy"
            alt=""
            loading="lazy"
            decoding="async"
          />
          <div
            class="caption mobile-caption md:hidden font-utility-meta-reg-02 text-text-tertiary pt-2 px-4 md:px-0"
          >
            top right mobile caption
          </div>
        </div>
        <div
          class="pane bottom-pane left-pane col-span-12 grid grid-cols-1 content-start md:col-span-6"
        >
          <img
            class="image bottom-image aspect-[16/12] w-full object-cover object-center"
            src="https://arc.stimg.co/startribunemedia/ANX6SDGLAE7WWGGYXW3GI2BI2Y.jpg?&w=800&ar=16:12&fit=crop&crop=entropy"
            alt=""
            loading="lazy"
            decoding="async"
          />
          <div
            class="caption mobile-caption md:hidden font-utility-meta-reg-02 text-text-tertiary pt-2 px-4 md:px-0"
          >
            bottom left mobile caption
          </div>
        </div>
        <div
          class="pane bottom-pane right-pane col-span-12 grid grid-cols-1 content-start md:col-span-6"
        >
          <img
            class="image bottom-image aspect-[16/12] w-full object-cover object-center"
            src="https://arc.stimg.co/startribunemedia/Y4IB6D6CRJQXM3XLQRPJZFHU4I.jpg?&w=800&ar=16:12&fit=crop&crop=entropy"
            alt=""
            loading="lazy"
            decoding="async"
          />
          <div
            class="caption mobile-caption md:hidden font-utility-meta-reg-02 text-text-tertiary pt-2 px-4 md:px-0"
          >
            bottom right mobile caption
          </div>
        </div>
      </div>
      <div
        class="caption desktop-caption col-span-full hidden md:block font-utility-meta-reg-02 text-text-tertiary pt-2"
      >
        4up gang caption for desktop.
      </div>
    </div>
  </GridRow>

  <GridRow variant={'inline'} additionalClasses={'gap-y-5'}>
    <h2 class="font-[graphik-bold] text-2xl">Inline photo blocks</h2>
    <h3 class="font-[graphik-semibold] text-lg">Inline single image</h3>
  </GridRow>

  <GridRow variant={'fullBleed'} additionalClasses={''}>
    <!-- single image -->

    <div
      class="inline-wrapper-19955451 rt-Box col-span-8 grid lg:grid-cols-12 gap-4 md:gap-6 lg:mx-auto grid-cols-8 col-span-full lg:print:mt-8 w-full max-w-[67.5rem] lg:gap-y-8 px-4 md:px-6 min-[1080px]:px-0 min-[1080px]:mx-auto"
    >
      <div
        class="photo-block relative container-19955451 inline-wrapper col-span-8 md:col-span-6 md:col-start-2 lg:col-start-4 rt-Box col-span-8 md:col-span-6 md:col-start-2 lg:col-start-4"
      >
        <div class="pane">
          <img
            class="image aspect-[16/9] w-full object-cover object-center"
            src="https://arc.stimg.co/startribunemedia/IYHTBHX5YNDWVFLZKMZLTDOAV4.jpg?&w=800&ar=16:9&fit=crop&crop=bottom"
            alt=""
            loading="lazy"
            decoding="async"
          />
          <div
            class="caption font-utility-meta-reg-02 text-text-tertiary pt-2 md:px-0"
          >
            single photo cutline.
          </div>
        </div>
      </div>
    </div>
  </GridRow>

  <GridRow variant={'inline'} additionalClasses={'gap-y-5'}>
    <Paragraph
      >Voluptate molestiae, perferendis iusto dolor officiis eaque cum quisquam
      quidem, doloremque dicta temporibus fuga ducimus voluptatum excepturi
      ratione laborum ab omnis quibusdam, accusamus vel eum culpa repellendus
      exercitationem. Fugit, consequatur!</Paragraph
    >
  </GridRow>
  <GridRow variant={'inline'} additionalClasses={'gap-y-5'}>
    <h3 class="font-[graphik-semibold] text-lg">Inline 2-up layout</h3>
  </GridRow>

  <GridRow variant={'fullBleed'} additionalClasses={''}
    ><!-- 2up test -->

    <div
      class="inline-wrapper-49000856 rt-Box col-span-8 grid lg:grid-cols-12 gap-4 md:gap-6 lg:mx-auto grid-cols-8 col-span-full lg:print:mt-8 w-full max-w-[67.5rem] lg:gap-y-8 px-4 md:px-6 min-[1080px]:px-0 min-[1080px]:mx-auto"
    >
      <div
        class="photo-block relative container-49000856 inline-wrapper col-span-8 md:col-span-6 md:col-start-2 lg:col-start-4"
      >
        <div
          class="panes col-span-full grid grid-cols-8 gap-x-[.5rem] gap-y-4 md:gap-y-[.5rem]"
        >
          <div
            class="pane left-pane col-span-8 grid grid-cols-1 content-start md:col-span-4"
          >
            <img
              class="image aspect-[9/8] w-full object-cover object-center"
              src="https://arc.stimg.co/startribunemedia/VVT2BOQXYVFININIVGKSVMLBEE.jpg?&w=800&ar=9:8&fit=crop&crop=entropy"
              alt=""
              loading="lazy"
              decoding="async"
            />
            <div
              class="caption mobile-caption md:hidden font-utility-meta-reg-02 text-text-tertiary pt-2 md:px-0"
            >
              Left mobile caption
            </div>
          </div>
          <div
            class="pane right-pane col-span-8 grid grid-cols-1 content-start md:col-span-4"
          >
            <img
              class="image aspect-[9/8] w-full object-cover object-center"
              src="https://arc.stimg.co/startribunemedia/ETRAQPBUTJH3BMRDYRU3MWEOLU.jpg?&w=800&ar=9:8&fit=crop"
              alt=""
              loading="lazy"
              decoding="async"
            />
            <div
              class="caption mobile-caption md:hidden font-utility-meta-reg-02 text-text-tertiary pt-2 md:px-0"
            >
              Right mobile caption
            </div>
          </div>
        </div>
        <div
          class="caption desktop-caption col-span-full hidden md:block font-utility-meta-reg-02 text-text-tertiary pt-2"
        >
          2up gang caption for desktop.
        </div>
      </div>
    </div></GridRow
  >

  <GridRow variant={'inline'} additionalClasses={'gap-y-5'}>
    <Paragraph
      >Voluptate molestiae, perferendis iusto dolor officiis eaque cum quisquam
      quidem, doloremque dicta temporibus fuga ducimus voluptatum excepturi
      ratione laborum ab omnis quibusdam, accusamus vel eum culpa repellendus
      exercitationem. Fugit, consequatur!</Paragraph
    >
  </GridRow>
  <GridRow variant={'inline'} additionalClasses={'gap-y-5'}>
    <h3 class="font-[graphik-semibold] text-lg">Inline 3-up layout</h3>
  </GridRow>

  <GridRow variant={'fullBleed'} additionalClasses={''}>
    <!-- 3up test -->

    <div
      class="inline-wrapper-76484583 rt-Box col-span-8 grid lg:grid-cols-12 gap-4 md:gap-6 lg:mx-auto grid-cols-8 col-span-full lg:print:mt-8 w-full max-w-[67.5rem] lg:gap-y-8 px-4 md:px-6 min-[1080px]:px-0 min-[1080px]:mx-auto"
    >
      <div
        class="photo-block relative container-76484583 inline-wrapper col-span-8 md:col-span-6 md:col-start-2 lg:col-start-4"
      >
        <div
          class="panes col-span-full grid grid-cols-8 gap-x-[.5rem] gap-y-4 md:gap-y-[.5rem]"
        >
          <div
            class="pane top-pane left-pane col-span-8 grid grid-cols-1 content-start md:col-span-4"
          >
            <img
              class="image top-image aspect-[16/16] w-full object-cover object-center"
              src="https://arc.stimg.co/startribunemedia/VEQFANTWDBHZZD3AWCQE3TMPEU.JPG?&w=800&ar=16:16&fit=crop&crop=left"
              alt=""
              loading="lazy"
              decoding="async"
            />
            <div
              class="caption mobile-caption md:hidden font-utility-meta-reg-02 text-text-tertiary pt-2 md:px-0"
            >
              Left mobile caption
            </div>
          </div>
          <div
            class="pane top-pane right-pane col-span-8 grid grid-cols-1 content-start md:col-span-4"
          >
            <img
              class="image top-image aspect-[16/16] w-full object-cover object-center"
              src="https://arc.stimg.co/startribunemedia/PVCAGYLU6RGVTKSV6BBVBMBEUI.JPG?&w=800&ar=16:16&fit=crop&crop=right"
              alt=""
              loading="lazy"
              decoding="async"
            />
            <div
              class="caption mobile-caption md:hidden font-utility-meta-reg-02 text-text-tertiary pt-2 md:px-0"
            >
              Right mobile caption
            </div>
          </div>
          <div
            class="pane bottom-pane col-span-8 grid grid-cols-1 content-start"
          >
            <img
              class="image bottom-image aspect-[16/9] w-full object-cover object-center"
              src="https://arc.stimg.co/startribunemedia/WPWXHD3ZXRCIHASIGUBZGYPEAE.JPG?&w=800&ar=16:9&fit=crop&crop=bottom"
              alt=""
              loading="lazy"
              decoding="async"
            />
            <div
              class="caption mobile-caption md:hidden font-utility-meta-reg-02 text-text-tertiary pt-2 md:px-0"
            >
              Bottom mobile caption
            </div>
          </div>
        </div>
        <div
          class="caption desktop-caption col-span-full hidden md:block font-utility-meta-reg-02 text-text-tertiary pt-2"
        >
          3up gang caption.
        </div>
      </div>
    </div>
  </GridRow>

  <GridRow variant={'inline'} additionalClasses={'gap-y-5'}>
    <Paragraph
      >Voluptate molestiae, perferendis iusto dolor officiis eaque cum quisquam
      quidem, doloremque dicta temporibus fuga ducimus voluptatum excepturi
      ratione laborum ab omnis quibusdam, accusamus vel eum culpa repellendus
      exercitationem. Fugit, consequatur!</Paragraph
    >
  </GridRow>
  <GridRow variant={'inline'} additionalClasses={'gap-y-5'}>
    <h3 class="font-[graphik-semibold] text-lg">Inline 3-up layout</h3>
  </GridRow>

  <GridRow variant={'fullBleed'} additionalClasses={''}>
    <!-- 4up -->

    <div
      class="inline-wrapper-16064936 rt-Box col-span-8 grid lg:grid-cols-12 gap-4 md:gap-6 lg:mx-auto grid-cols-8 col-span-full lg:print:mt-8 w-full max-w-[67.5rem] lg:gap-y-8 px-4 md:px-6 min-[1080px]:px-0 min-[1080px]:mx-auto"
    >
      <div
        class="photo-block relative container-16064936 col-span-8 md:col-span-6 md:col-start-2 lg:col-start-4"
      >
        <div
          class="panes col-span-full grid grid-cols-8 gap-x-[.5rem] gap-y-4 md:gap-y-[.5rem]"
        >
          <div
            class="pane top-pane left-pane col-span-8 grid grid-cols-1 content-start md:col-span-4"
          >
            <img
              class="image top-image aspect-[16/12] w-full object-cover object-center"
              src="https://arc.stimg.co/startribunemedia/TSU46NVOFNO5YTLML34IQK3YQA.jpg?&w=800&ar=16:12&fit=crop&crop=top"
              alt=""
              loading="lazy"
              decoding="async"
            />
            <div
              class="caption mobile-caption md:hidden font-utility-meta-reg-02 text-text-tertiary pt-2 md:px-0"
            >
              top left mobile caption
            </div>
          </div>
          <div
            class="pane top-pane right-pane col-span-8 grid grid-cols-1 content-start md:col-span-4"
          >
            <img
              class="image top-image aspect-[16/12] w-full object-cover object-center"
              src="https://arc.stimg.co/startribunemedia/RUUTDFV6YY65XAOXGDQQSY7GCE.jpg?&w=800&ar=16:12&fit=crop&crop=entropy"
              alt=""
              loading="lazy"
              decoding="async"
            />
            <div
              class="caption mobile-caption md:hidden font-utility-meta-reg-02 text-text-tertiary pt-2 md:px-0"
            >
              top right mobile caption
            </div>
          </div>
          <div
            class="pane bottom-pane left-pane col-span-8 grid grid-cols-1 content-start md:col-span-4"
          >
            <img
              class="image bottom-image aspect-[16/12] w-full object-cover object-center"
              src="https://arc.stimg.co/startribunemedia/ANX6SDGLAE7WWGGYXW3GI2BI2Y.jpg?&w=800&ar=16:12&fit=crop&crop=entropy"
              alt=""
              loading="lazy"
              decoding="async"
            />
            <div
              class="caption mobile-caption md:hidden font-utility-meta-reg-02 text-text-tertiary pt-2 md:px-0"
            >
              bottom left mobile caption
            </div>
          </div>
          <div
            class="pane bottom-pane right-pane col-span-8 grid grid-cols-1 content-start md:col-span-4"
          >
            <img
              class="image bottom-image aspect-[16/12] w-full object-cover object-center"
              src="https://arc.stimg.co/startribunemedia/Y4IB6D6CRJQXM3XLQRPJZFHU4I.jpg?&w=800&ar=16:12&fit=crop&crop=entropy"
              alt=""
              loading="lazy"
              decoding="async"
            />
            <div
              class="caption mobile-caption md:hidden font-utility-meta-reg-02 text-text-tertiary pt-2 md:px-0"
            >
              bottom right mobile caption
            </div>
          </div>
        </div>
        <div
          class="caption desktop-caption col-span-full hidden md:block font-utility-meta-reg-02 text-text-tertiary pt-2"
        >
          4up gang caption for desktop.
        </div>
      </div>
    </div>
  </GridRow>

  <GridRow variant={'inline'} additionalClasses={'gap-y-5'}>
    <Paragraph
      >Voluptate molestiae, perferendis iusto dolor officiis eaque cum quisquam
      quidem, doloremque dicta temporibus fuga ducimus voluptatum excepturi
      ratione laborum ab omnis quibusdam, accusamus vel eum culpa repellendus
      exercitationem. Fugit, consequatur!</Paragraph
    >
  </GridRow>
</Grid>

<style>
  a {
    text-decoration-line: underline;
    text-decoration-color: #00854b;
    text-underline-offset: 2px;
  }

  a:hover {
    color: #00854b;
  }
</style>
