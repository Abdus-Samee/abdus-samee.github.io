---
title: My Gallery
show_profile: true
images:
 - /portfolio/theme/img/avatar.jpg
 - /portfolio/theme/img/gal2n.jpg
 - /portfolio/theme/img/fb_recep.jpg
 - /portfolio/theme/img/fb_tour1.jpg
 - /portfolio/theme/img/fb_tour2.jpg
 - /portfolio/theme/img/fb_bdpho.jpg
 - /portfolio/theme/img/fb_tour3.jpg
 - /portfolio/theme/img/gal3.jpg
 - /portfolio/theme/img/fb_college.jpg
---

<style>
  .zoom{
  transition: transform .2s;
  }
  .zoom:hover{
    -ms-transform: scale(1.5);
    -webkit-transform: scale(1.5);
    transform: scale(1.5);
  }
</style>

My collection of gallery.


<div style="visibility:hidden;" class="card-columns">
    {% for img in page.images %}
    <div style="overflow:hidden;" class="card img-thumbnail" data-toggle="modal" data-target="#exampleModal" data-img="{{ img }}">
        <img class="card-img-top zoom" src="{{ img }}" />
    </div>
    {% endfor %}
</div>

<div class="modal fade" id="exampleModal">
  <div class="modal-dialog modal-lg modal-dialog-centered">
    <div class="modal-content w-75">
      <div class="modal-header">
        <button type="button" class="close" data-dismiss="modal" aria-label="Close">
          <span aria-hidden="true">&times;</span>
        </button>
      </div>
      <div class="modal-body">
        <div id="carouselExampleControls" class="carousel slide mb-4" data-ride="carousel">
          <div class="carousel-inner">
            {% for img in page.images %}
              <div class="carousel-item">
                <img src="{{ img }}" class="d-block w-100" alt="">
              </div>
            {% endfor %}
          </div>
          <a class="carousel-control-prev" href="#carouselExampleControls" role="button" data-slide="prev">
            <span class="carousel-control-prev-icon" aria-hidden="true"></span>
            <span class="sr-only">Previous</span>
          </a>
          <a class="carousel-control-next" href="#carouselExampleControls" role="button" data-slide="next">
            <span class="carousel-control-next-icon" aria-hidden="true"></span>
            <span class="sr-only">Next</span>
          </a>
        </div>
      </div>
    </div>
  </div>
</div>

<script type="text/javascript">
  $(document).ready(function() {
    $('.card-columns').css('visibility', 'visible')  
  })
    $('#exampleModal').on('show.bs.modal', function (event) {
      var active = document.querySelector('.active')
      if(active != null){
        active.classList.remove('active')
        console.log('Removed...')
        console.log(active)
      }
      var arr = $('.carousel-item')
      for(var i = 0; i < arr.length; i++){
        if(arr[i].className.includes('active')){
          console.log('Holds...')
          console.log(arr[i])
        }
      }
      var button = $(event.relatedTarget)
      var img = button.data('img')
      for(var i = 0; i < arr.length; i++){
        if(arr[i].innerHTML.includes(img)){
          arr[i].classList.add('active')
        }
      }
    })
</script>
