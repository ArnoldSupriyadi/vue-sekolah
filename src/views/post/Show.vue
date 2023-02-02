<template>
  <div id="post-detail">
    <!-- header -->
    <Header />
    <!-- end of heder -->

    <!-- main content -->
    <header class="pt-5 border-bottom bg-light">
      <div class="container pt-md-1">
        <h1 class="bd-title mt-4 font-weight-bold">
          <i class="fa fa-book-open" aria-hidden="true"></i> BERITA
        </h1>
        <p class="bd-lead">{{ post.title }}</p>
      </div>
    </header>

    <!-- breadcrumb -->
    <nav aria-label="breadcrumb">
      <ol class="breadcrumb">
        <li class="breadcrumb-item">
          <router-link :to="{ name: 'home' }" class="text-decoration-none"
            ><i class="fa fa-home"></i> Home</router-link
          >
        </li>
        <li class="breadcrumb-item">
          <router-link :to="{ name: 'post' }" class="text-decoration-none"
            ><i class="fa fa-book-open"></i>Berita</router-link
          >
        </li>
        <li class="breadcrumb-item active" aria-current="page">
          {{ post.title }}
        </li>
      </ol>
    </nav>
    <!-- end breadcrumb -->

    <div class="container-fluid mt-5 mb-5">
      <div class="row">
        <div class="col-md-8">
          <div v-if="post.title">
            <div class="card border-0 shadow-sm rounded">
              <div class="card-body">
                <h3>{{ post.title }}</h3>
                <hr />
                <img :src="post.image" class="w-100 rounded" />

                <div class="mt-3" v-html="post.content"></div>
              </div>
            </div>
          </div>

          <div v-else>
            <div class="card border-0 shadow-sm rounded">
              <div class="card-body">
                <FacebookLoader />
              </div>
            </div>
          </div>
        </div>

        <div class="col-md-4">
          <!-- agenda section -->
          <div class="title mb-4">
            <h4>
              <i class="fa fa-calendar" aria-hidden="true"></i> AGENDA TERBARU
            </h4>
          </div>

          <div v-if="events.length > 0">
            <router-link :to="{ name: 'detail_event', params:{slug: event.slug}}" v-for="event in events" :key="event.id" class="text-decoration-none text-dark">
                <div class="card mb-3 shadow-sm border-0">
                    <div class="card-body">
                        <h6>{{ event.title }}</h6>
                        <hr>
                        <div>
                            
                        </div>
                    </div>
                </div>
            </router-link>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "PostDetailComponent",
  setup() {},
};
</script>