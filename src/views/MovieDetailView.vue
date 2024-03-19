<script setup>

</script>
<template>
 <!-- Overview -->

 <section id="movie__overview" class="row position:relative" ref="overview" >

<!-- Background Trailer -->

<section class="p-0 top-0 start-0 bottom-0 end-0">
    <div>
        <video style="object-fit: cover; backdrop-filter: brightness(60%);" class="full-screen-element col-12" id="trailerVideo" oncontextmenu="return false;" autoplay muted loop disablePictureInPicture>
            <source src = "https://localhost:7071/uploads/videos/movieTrailers/da61bf1a-4a62-4ee6-a524-d7bab2e3d283_The Nun II.mp4">
        </video>
    </div>
</section>

<!-- Movie Detail -->
<section class="position-absolute start-0 end-0 fullscreen-height px-0 col-12" style="background: linear-gradient(to top, rgb(0, 0, 0), rgba(0, 0, 0, 0.444));">

    <!-- Information of movie -->

    <div class="position-relative top-50 start-50 translate-middle col-12">

        <!-- Overview Tags -->
        <div class="row mt-5">
            <div class="col-12 d-flex justify-content-center">
                <div class="col-1 text-center">
                    <span class="border text-light p-2 rounded-2">18+</span>
                </div>
                <div class="col-1 text-center">
                    <span class="text-light p-2">2023</span>
                </div>
                <div class="col-1 text-center">
                    <span class="text-light p-2">180 Min</span>
                </div>
                <div class="col-1 text-center">
                    <span class="text-light p-2">
                            English - VietSub
                    </span>
                </div>
            </div>
        </div>

        <!-- Movie logo -->
        <div class="row">
            <div class="col-12 d-block">
                <img class="col-4 d-block my-5 mx-auto" style="width: 30vmax" src="https://localhost:7071/uploads/images/movies/logos/066c6785-0176-45fd-b11e-5ac5ea2a21c0_The Nun II.png" alt="">
            </div>
        </div>

        <div class="row col-12 ps-5">
            <!-- Movie tags -->
            <div class="">

                <!-- @foreach($movie_cate as $movie_cate) -->

                <span class="border me-2 text-light px-3 py-2 fs-5 rounded-2">Horror</span>

                <!-- @endforeach -->

            </div>

            <div class="d-flex justify-content-between">
                <!-- Movie Detail -->
                <div class="col-5 mt-4">
                    <span class="text-light fs-3" style="font-family: 'Poppins', sans-serif;">
                        The NUN II
                    </span>
                </div>

                <!-- Sound Button -->
                <div @click="toggleSound" class="col-1">
                    <div ref="soundButton" class="sound-button d-inline-block text-light position-relative top-50 start-50 translate-middle" style="font-size: 1.5em; cursor: pointer;">
                      <i class="fas" :class="soundIcon"></i> sound
                    </div>
                </div>
            </div>

            <!-- Option -->
            <div class="mt-4">
                <span class="border rounded-pill text-light text-center px-3 py-2 fs-5" @click="toDetailedPage"  style="cursor: pointer;">
                    <i class="fa-solid fa-circle-info me-1"></i>  More 
                </span>
                <span class="border rounded-pill text-light text-center mx-3 px-3 py-2 fs-5" @click="toBookTickerPage" style="cursor: pointer;">
                    <i class="fa-solid fa-ticket" style="color: #ffffff;"></i>  Book Tickets 
                </span>
            </div>

        </div>
    </div>

</section>

</section>

<!-- More Detail Of The Movie -->

<section id="movie__full--detail" class="row full-height px-5 mb-5" ref="detail">

<!-- Back Button -->
<div class="" style="margin-top: 5.5vmax;">
    <span @click="toOverviewPage" class="border rounded-pill text-light text-center px-3 py-2 fs-5" style="cursor: pointer;">
        <i class="fa-solid fa-backward"></i>  Back 
    </span>
</div>

<!-- Information about the movie -->
<section class="d-flex">

    <!-- Movie text in4 -->
    <div class="col-7 hide-scrollbar" style="height: 35vmax; overflow-x: hidden; overflow-y: scroll;">

        <p class="text-light" style="font-size: 2.5vmax; font-family: 'Poppins', sans-serif;">The NUN II</p>

        <span class="border me-2 text-light px-3 py-2 fs-5 rounded-2">
            
            <span class="pe-2 fw-bold">IMDb </span>

        <span class="border-start py-2 ps-2 text-light"> 5/5 </span>
        </span>

        <span class="border rounded-pill text-light text-center mx-2 px-3 py-2 fs-5" @click="toBookTickerPage" style="cursor: pointer;">
                <i class="fa-solid fa-ticket" style="color: #ffffff;"></i>  Book Tickets 
        </span>
        <p class="text-light mt-4">
            âsjd
        </p>

        <!-- Actor and Director -->
        <section>

            <!-- Actors -->
            <div>
                <span class="text-light" style="font-size: 1.7vmax;"> Actors </span>


                <div class="d-flex my-4">
                    <!-- @foreach($movie_actor as $movie_actor) -->
                    <a href="">
                        <img class="d-block me-5" src="https://localhost:7071/uploads/images/casts/478768e4-3afd-4ecd-9955-b7cba0447062_nhgjkl.png" style="object-fit: cover; border-radius: 50%; overflow: hidden; height: 6vmax; width: 6vmax;" alt="">
                    </a>
                    <!-- @endforeach -->
                </div>


            </div>

            <!-- Director -->
            <div>
                <span class="text-light" style="font-size: 1.7vmax;"> Directors </span>
                <div class="d-flex my-4 ">
                    <!-- @foreach($movie_director as $movie_director) -->
                    <a href="">
                        <img class="d-block  me-3" src="https://localhost:7071/uploads/images/casts/478768e4-3afd-4ecd-9955-b7cba0447062_nhgjkl.png" style="object-fit: cover; border-radius: 50%; overflow: hidden; height: 6vmax; width: 6vmax;" alt="">
                    </a>
                    <!-- @endforeach -->
                </div>
            </div>

        </section>

        <!-- Related Movies -->
        <section>

            <span class="text-light" style="font-size: 1.7vmax;"> Related Movies </span>


            <div class="mt-4 d-flex col-12 border border-0  hide-scrollbar" style="overflow-x: scroll;">

                <!-- @foreach($related_movie as $related_movie) -->
                <a href="">
                    <img class="border border-0  me-4" style="height: 13vmax; width: 23vmax; object-fit: cover;opacity:0.9; border-radius :1vmax" src="https://localhost:7071/uploads/images/movies/thumbnails/6d6e92fa-0820-4938-98b0-fb298c5819ec_The Nun II.png" alt="">
                </a>
                <a href="">
                    <img class="border border-0  me-4" style="height: 13vmax; width: 23vmax; object-fit: cover;opacity:0.9; border-radius :1vmax" src="https://localhost:7071/uploads/images/movies/thumbnails/6d6e92fa-0820-4938-98b0-fb298c5819ec_The Nun II.png" alt="">
                </a>
                <a href="">
                    <img class="border border-0  me-4" style="height: 13vmax; width: 23vmax; object-fit: cover;opacity:0.9; border-radius :1vmax" src="https://localhost:7071/uploads/images/movies/thumbnails/6d6e92fa-0820-4938-98b0-fb298c5819ec_The Nun II.png" alt="">
                </a>
                <a href="">
                    <img class="border border-0  me-4" style="height: 13vmax; width: 23vmax; object-fit: cover;opacity:0.9; border-radius :1vmax" src="https://localhost:7071/uploads/images/movies/thumbnails/6d6e92fa-0820-4938-98b0-fb298c5819ec_The Nun II.png" alt="">
                </a>
                <a href="">
                    <img class="border border-0  me-4" style="height: 13vmax; width: 23vmax; object-fit: cover;opacity:0.9; border-radius :1vmax" src="https://localhost:7071/uploads/images/movies/thumbnails/6d6e92fa-0820-4938-98b0-fb298c5819ec_The Nun II.png" alt="">
                </a>
                <!-- @endforeach -->

            </div>

        </section>

    </div>

    <!-- Movie Img -->
    <div class="col-5 d-flex justify-content-end">
        <img class="col-12 border rounded-3 border-0 " src="https://localhost:7071/uploads/images/movies/posters/0c182537-fbe9-4a11-96ac-8d7368f44651_The Nun II.png" alt="" style="object-fit: cover;height: 35vmax; width: 25vmax;">
    </div>

</section>

</section>


<!-- Ticket -->

<section id="book__ticket" class="row full-height-ticket px-5" ref="ticket">
  <section class=" full-height" >
      <span  @click="toDetailedPage" class="border rounded-pill text-light text-center px-3 py-2 fs-5" style="cursor: pointer;">
              <i class="fa-solid fa-backward"></i>  Back 
      </span>
      <div  class="col-10 d-flex flex-wrap mx-auto hide-scrollbar mt-2 mb-5" style="height: 85%; overflow-x: hidden; overflow-y: scroll;">
          <div class="card bg-dark text-light col-3 me-5 mx-5 py-3 mt-3 px-5 text-center" style="border-radius: 1vmax; height: 40%;">
              <div class="card-header text-danger">
                  <h2 class="mb-0 fw-bolder">
                      Room 1
                  </h2>
              </div>
              <div class="card-body">
                  <h4 class="card-title mb-3">26-12-2024</h4>
                  <p class="card-text fs-5"><b>Start time:</b> 20:00</p>
                  <p class="card-text fs-5"><b>End time:</b> 22:00</p>
                  <a href="orderTickets.html" class="btn btn-danger mt-3 py-2 px-5 border border-0 rounded-pill">Booking ticket</a>
              </div>
          </div>
          <div class="card bg-dark text-light col-3 me-5 mx-5 py-3 mt-3 px-5 text-center" style="border-radius: 1vmax; height: 40%;">
              <div class="card-header text-danger">
                  <h2 class="mb-0 fw-bolder">
                      Room 1
                  </h2>
              </div>
              <div class="card-body">
                  <h4 class="card-title mb-3">26-12-2024</h4>
                  <p class="card-text fs-5"><b>Start time:</b> 20:00</p>
                  <p class="card-text fs-5"><b>End time:</b> 22:00</p>
                  <a href="orderTickets.html" class="btn btn-danger mt-3 py-2 px-5 border border-0 rounded-pill">Booking ticket</a>
              </div>
          </div>
          <div class="card bg-dark text-light col-3 me-5 mx-5 py-3 mt-3 px-5 text-center" style="border-radius: 1vmax; height: 40%;">
              <div class="card-header text-danger">
                  <h2 class="mb-0 fw-bolder">
                      Room 1
                  </h2>
              </div>
              <div class="card-body">
                  <h4 class="card-title mb-3">26-12-2024</h4>
                  <p class="card-text fs-5"><b>Start time:</b> 20:00</p>
                  <p class="card-text fs-5"><b>End time:</b> 22:00</p>
                  <a href="orderTickets.html" class="btn btn-danger mt-3 py-2 px-5 border border-0 rounded-pill">Booking ticket</a>
              </div>
          </div>
          <div class="card bg-dark text-light col-3 me-5 mx-5 py-3 mt-3 px-5 text-center" style="border-radius: 1vmax; height: 40%;">
              <div class="card-header text-danger">
                  <h2 class="mb-0 fw-bolder">
                      Room 1
                  </h2>
              </div>
              <div class="card-body">
                  <h4 class="card-title mb-3">26-12-2024</h4>
                  <p class="card-text fs-5"><b>Start time:</b> 20:00</p>
                  <p class="card-text fs-5"><b>End time:</b> 22:00</p>
                  <a href="orderTickets.html" class="btn btn-danger mt-3 py-2 px-5 border border-0 rounded-pill">Booking ticket</a>
              </div>
          </div>
          <div class="card bg-dark text-light col-3 me-5 mx-5 py-3 mt-3 px-5 text-center" style="border-radius: 1vmax; height: 40%;">
              <div class="card-header text-danger">
                  <h2 class="mb-0 fw-bolder">
                      Room 1
                  </h2>
              </div>
              <div class="card-body">
                  <h4 class="card-title mb-3">26-12-2024</h4>
                  <p class="card-text fs-5"><b>Start time:</b> 20:00</p>
                  <p class="card-text fs-5"><b>End time:</b> 22:00</p>
                  <a href="orderTickets.html" class="btn btn-danger mt-3 py-2 px-5 border border-0 rounded-pill">Booking ticket</a>
              </div>
          </div>
      </div>
  </section>
</section>

</template>
<script>
export default {
  data() {
    return {
      overviewPage: 0,
      detailedPage: 0,
      BookTickerPage: 0,
      isMuted: false
    };
  },
  mounted() {
    const overviewPage = this.$refs.overview ? this.$refs.overview.getBoundingClientRect().top + window.scrollY : 0;
    const detailedPage = this.$refs.detail ? this.$refs.detail.getBoundingClientRect().top + window.scrollY : 0;
    const ticketPage = this.$refs.ticket ? this.$refs.ticket.getBoundingClientRect().top + window.scrollY : 0;

    this.$data.overviewPage = overviewPage;
    this.$data.detailedPage = detailedPage;
    this.$data.ticketPage = ticketPage;
    window.addEventListener('resize', this.setElementHeights);
    this.setElementHeights();
    document.body.style.overflow = "hidden";
  },
  methods: {
    toggleSound() {
      const trailer = document.getElementById('trailerVideo');
      trailer.muted = !trailer.muted;
      if (trailer.muted) {
        this.$refs.soundButton.innerHTML = '<i class="fas fa-volume-xmark"></i> sound';
      } else {
        this.$refs.soundButton.innerHTML = '<i class="fas fa-volume-high"></i> sound';
      }
    },
    toOverviewPage() {
      console.log('toOverviewPage');
      window.scroll({
        top: this.overviewPage,
        behavior: 'smooth'
      });
    },
    toDetailedPage() {
      console.log('toDetailedPage');
      window.scroll({
        top: this.detailedPage,
        behavior: 'smooth'
      });
    },
    toBookTickerPage() {
      console.log('toBookTickerPage');
      window.scroll({
        top: this.ticketPage,
        behavior: 'smooth'
      });
    },
    setElementHeights() {
      const win = window,
        docElem = win.document.documentElement,
        x = win.innerWidth || docElem.clientWidth,
        y = win.innerHeight || docElem.clientHeight;

        const elements = document.querySelectorAll('.full-screen-element, .fullscreen-height, .full-height, .full-height-ticket');

        elements.forEach(element => {
            if (element) { // Kiểm tra xem phần tử có tồn tại không
                element.style.height = `${y}px`;
            }
        });
    },
  },
  beforeDestroy() {
    window.removeEventListener('resize', this.setElementHeights); // Loại bỏ lắng nghe sự kiện trước khi component bị hủy
    document.body.style.overflow = "";
  },
  computed: {
    soundIcon() {
      return this.isMuted ? "fa-volume-xmark" : "fa-volume-high";
    }
  },
};
</script>
