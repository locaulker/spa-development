<template>
  <div><!-- Start Parent Element -->

    <app-main-nav></app-main-nav>

    <div class="container">
      <div class="row">
        <div class="col-sm-8 col-sm-offset-2">

          <app-post-excerpt v-for="post in posts" :key="post.id" :post="post"></app-post-excerpt>

          <nav>
            <ul class="pager">
              <li><a href="#">Previous</a></li>
              <li><a href="#">Next</a></li>
            </ul>
          </nav>

        </div><!-- /.blog-main -->
      </div><!-- /.row -->
    </div><!-- /.container -->

    <app-footer></app-footer>

  </div><!-- End Parent Element -->
</template>

<script>
export default {
  data: function() {
    return {
      posts:    []
    }
  },
  mounted: function() {
    // var self = this;
   jQuery.get(wp_rest_api.base_url + 'posts').always((response) => {
      this.posts    = response;
    });
  }
}
</script>

<style>
</style>
