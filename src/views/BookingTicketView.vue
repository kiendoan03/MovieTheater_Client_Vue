<script setup>
    import router from '@/router';
import { library } from '@fortawesome/fontawesome-svg-core'
    import { fas } from '@fortawesome/free-solid-svg-icons'
    import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome'

    library.add(fas)
</script>
<template>
         <div  class="row p-3 mt-5 pt-5">
            <div class="col-7" v-if="model.schedule.room.roomTypeId == 1">
                <div class="row screen mb-5">
                    <img src="../assets/image/bg-screen.png" class="object-fit: cover; width: 100%;" alt="">
                </div>
                <div class="row seat d-flex col-12 " style="margin-top: 1vmax;">
                    <div class="col-1">
                        <div class="row">
                            <div class="col-12 text-center  fw-bolder fs-5" style="height: 2.4vmax;">
                            </div>
                            <div class="col-12 text-center text-secondary fw-bolder fs-5" style="height: 4.8vmax;">
                                A
                            </div>
                            <div class="col-12 text-center text-secondary fw-bolder fs-5" style="height: 4.8vmax;">
                                B
                            </div>
                            <div class="col-12 text-center text-secondary fw-bolder fs-5" style="height: 4.8vmax;">
                                C
                            </div>
                            <div class="col-12 text-center text-secondary fw-bolder fs-5" style="height: 4.8vmax;">
                                D
                            </div>
                            <div class="col-12 text-center text-secondary fw-bolder fs-5" style="height: 4.8vmax;">
                                E
                            </div>
                            <div class="col-12 text-center text-secondary fw-bolder fs-5" style="height: 4.8vmax;">
                                F
                            </div>
                        </div>
                    </div>
                    <div class="col-11">
                        <div class="row mb-3">
                            <div class="col-1 text-center text-secondary fw-bolder fs-5">
                                1
                            </div>
                            <div class="col-1 text-center text-secondary fw-bolder fs-5">
                                2
                            </div>
                            <div class="col-1 text-center text-secondary fw-bolder fs-5">
                                3
                            </div>
                            <div class="col-1 text-center text-secondary fw-bolder fs-5">
                                4
                            </div>
                            <div class="col-1 text-center text-secondary fw-bolder fs-5">
                                5
                            </div>
                            <div class="col-1 text-center text-secondary fw-bolder fs-5">
                                6
                            </div>
                            <div class="col-1 text-center text-secondary fw-bolder fs-5">
                                7
                            </div>
                            <div class="col-1 text-center text-secondary fw-bolder fs-5">
                                8
                            </div>
                            <div class="col-1 text-center text-secondary fw-bolder fs-5">
                                9
                            </div>
                            <div class="col-1 text-center text-secondary fw-bolder fs-5">
                                10
                            </div>
                            <div class="col-1 text-center text-secondary fw-bolder fs-5">
                                11
                            </div>
                            <div class="col-1 text-center text-secondary fw-bolder fs-5">
                                12
                            </div>
                        </div>
                        <div class="row">
                            <div v-for="seat in model.tickets" :key="seat.id" class="col-1">
                                <button @click="orderTicket(seat.id, this.model.auth)" v-if="seat.seats.seatTypeId == 1 && seat.status == 0 " type="button" class="btn btn-none shadow-none col-12">
                                    <div class="col-12 text-center mb-5">
                                        <img style="width: 1.5vmax;" src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAB4AAAAeCAYAAAA7MK6iAAAACXBIWXMAAAsTAAALEwEAmpwYAAAAr0lEQVR4nO2QQQrCMBBFc4EWdO+6Z5FuCsVLSsE72Eu4rt0q6AWeBFIRaWxnmkKlecsh89/kGxNZLcAOqIAncuzOCcg00hvTudssidj+NBRHiVhTr4+HRByUKP5VdQIUwGVCww1Q2qzRVX8csHEBGulWIsqBFrgCezc7KMSlL68X9+B9tZulCnHiy+vle9s3H2Iob/liLf8nDo2J4o71Vm0CM0ZcA+cZxPUcuZFl8wJRIS97SX64DQAAAABJRU5ErkJggg==">
                                    </div>
                                </button>
                                <button  @click="orderTicket(seat.id, this.model.auth)"  v-if="seat.seats.seatTypeId == 1 && seat.status == 1 && seat.customerId == this.model.auth" type="button"  class="btn btn-none shadow-none col-12">
                                    <div class="col-12 text-center mb-5">
                                        <img style="width: 1.5vmax;" src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAB4AAAAeCAYAAAA7MK6iAAAACXBIWXMAAAsTAAALEwEAmpwYAAAA5klEQVR4nO2UUQqCQBCGvUDFjM89dxNnRIggOl2Rs0ovIXSHukTP1WtBXaDYyAhyaVctivxgXkT/b/1x9LyGvwWmQRcUZ6DohIrPLqOfAaGFn1LPWYqK967CpxE66Cx7seKssvQu57mD2L1eY+1CR2txbW97m0ZsxJ/0W34SDkB4XaHiDcbBUGdZV53TmUVwDSghbY8DtBZBTBEo2oHQFiQMrx9awiNncRwMTXmF6BseT62vYcptV3Feb1FeIaY1KLs+1muF3yYuy++J8VO/TmzE6l+q9mrmtVhohcLL2sXyntyG7+YCA4EH4/PVpiIAAAAASUVORK5CYII=">
                                    </div>
                                </button>
                                <button v-if="seat.seats.seatTypeId == 1 && seat.status == 1 && seat.customerId != this.model.auth" disabled type="button"  class="btn btn-none shadow-none border-0 col-12">
                                    <div class="col-12 text-center mb-5">
                                        <img style="width: 1.5vmax;" src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAB4AAAAeCAYAAAA7MK6iAAAACXBIWXMAAAsTAAALEwEAmpwYAAAA4ElEQVR4nO2UQQrCMBBFewErzbh17VnEjVC8pAjeQW8gwowtmWJ1q6AXqAwoCjaQpFWU5sPfhPa/zi+TKArqrJI8HwLTQjFdgalysbyjNC6BceQO1XRyBb5Z01myrMEyaWPo03NrsE+9ZuPFZeKqTQewuWrEHhQ0VZqowb8tlcZUsqyrfqi/3yQS4AONy62yBg30bgIaj8B4SAoay5limjlfIBpTU16t5IHXr5YzlWWx88T3euvyamVaA9/1sV4r+DWwr/4PDN+6OiGAuStVRy3LAoxrxbhqH4wfyQ36bd0A+6VLYy4GIYQAAAAASUVORK5CYII=">
                                    </div>
                                </button>
                                <button v-if="seat.seats.seatTypeId == 1 && seat.status == 2 && seat.customerId == this.model.auth" disabled class="btn btn-none border-0 shadow-none col-12">
                                    <div class="col-12 text-center mb-5">
                                        <img style="width: 1.5vmax;" src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAB4AAAAeCAYAAAA7MK6iAAAACXBIWXMAAAsTAAALEwEAmpwYAAAA5klEQVR4nO2UUQqCQBCGvUDFjM89dxNnRIggOl2Rs0ovIXSHukTP1WtBXaDYyAhyaVctivxgXkT/b/1x9LyGvwWmQRcUZ6DohIrPLqOfAaGFn1LPWYqK967CpxE66Cx7seKssvQu57mD2L1eY+1CR2txbW97m0ZsxJ/0W34SDkB4XaHiDcbBUGdZV53TmUVwDSghbY8DtBZBTBEo2oHQFiQMrx9awiNncRwMTXmF6BseT62vYcptV3Feb1FeIaY1KLs+1muF3yYuy++J8VO/TmzE6l+q9mrmtVhohcLL2sXyntyG7+YCA4EH4/PVpiIAAAAASUVORK5CYII=">
                                    </div>
                                </button>
                                <button v-if="seat.seats.seatTypeId == 1 && seat.status == 2 && seat.customerId != this.model.auth" disabled class="btn btn-none border-0 shadow-none col-12">
                                    <div class="col-12 text-center mb-5">
                                        <img style="width: 1.5vmax;" src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAB4AAAAeCAYAAAA7MK6iAAAACXBIWXMAAAsTAAALEwEAmpwYAAAA4UlEQVR4nO2UQQrCMBBFewEF68JJUbeeRdwIxUuK4BnsRPEIrq1bBd1OIJKKUrCVSVql0nyYTWj/m/lkEgRerZXeRCOFYkUobkoKbVOPf2CtZTSxhhLC2Rb41oCEi/Fig82kVaG5WrLBLvF+iP3Kn7i+abPy4FJp2e9QIuaEcKhwo48kITZe7KhfDeC4ZwxcoHo3DNkg2g5mhHAihJQQptlFQ1g4gOMyv0KZD/JdmzO9D7u24Ge8RX6FKlsD1/Vhr5VqGthV/wdWv3o6lQfLtkQd1CwGGFAhJPWD4Su+Xs3WHaGYZJrSMa3iAAAAAElFTkSuQmCC">
                                    </div>
                                </button>
                            </div>
                        </div>
                        <div class="row">
                            <div v-for="seat in model.tickets" :key="seat.id" class="col-1">
                                <button v-if="seat.seats.seatTypeId == 2 && seat.status == 0" type="button"  class="btn btn-none shadow-none col-12">
                                    <div  @click="orderTicket(seat.id, this.model.auth)"  class="col-12 text-center mb-5">
                                        <img style="width: 1.5vmax;" src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADIAAAAyCAYAAAAeP4ixAAAACXBIWXMAAAsTAAALEwEAmpwYAAAC3klEQVR4nO2ZS2xNQRjH+2AtoYIGi6ZRUY+VhJSVakKIRyXUVoSdZ1KxsusOVeq5IPFohERiZWHhkXhtPBMb9SoRxOaqaNGffPK/nFztvWfmnnvuIee3anpmvu/7z3wz883cioqUlJSUlJSUlH8XYBSwBjgBPAE+AENEh9kym4+B40Cr+YxaRBvwgvh5DqyNQkC1RqfcHAOqihFyhOTQ7StiNcljhU9KlWNNFKLXYnMRspTk0uIi5CjJpdtFyF2Sy20XITXAaKAWaAa6gEwZgs7I9yLFYjHVhBYygrgJwPkYRfSYT99gF8rAG2AA6APOAQv0vRLoiEFEh/kKE9NwddThAsYPqV1liWemRz5CxxQUUqjD745qP7FEayaTTSfXmLJT50KT+h0kerq8Y9JUunBWzhYTPc2y7R6TFpELfXJm22HU1Mq2e0zaCVz4biW16rEfRIfZqpZt8+HCgAl56+F0nEbuPdHxTjbHe/Tt88lHY4mcXiI6LhZRsP5aI00ed+9OOZ2j0rpYngEzZfOAY1+LfX52C+507PwZmOZVPuSvLBqAfsdY9gcNVHmIeQ2sK7qI+1OkLgPqgKnArZAzsW/Yu7xNEXCG8mD11WaVP4XWyWlgXpgRihsb3XrgAfBNZ9TLkRq7THUcPAVO6b6xHZgb+LYDWAXs1YPgteCZlSQhj4ApwDZgj3L9Ts7DnKVaO7AJmCVRiRNyFWjUE2mYtNsI7EqikGz6TAbuFSjrW3XWffIR8iUeLZwExuakVfCsatRsBOvBQRchD4mP6Xrdz2VIF7jc3avXRUjY21mxvAImBUqkj8D9wPc27Wx/3whDCqn3KKV9sINtvf62BwUTNQbYDXzVLwEbAu3tjKkLLURibG8vNZdVX7UAs/UwaKm0HJgBrAS2BNpvdRIRENOukSklF5Q+gzn/v6Kn237FsNNLRECMjVi5aShKREBMXpJu/78UcjOPn+sltn8jjJGfT8zJxA5Aeb8AAAAASUVORK5CYII=">
                                    </div>
                                </button>
                                <button  @click="orderTicket(seat.id, this.model.auth)"  v-if="seat.seats.seatTypeId == 2 && seat.status == 1 && seat.customerId == this.model.auth" type="button"  class="btn btn-none shadow-none col-12">
                                    <div class="col-12 text-center mb-5">
                                        <img style="width: 1.5vmax;" src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADIAAAAyCAYAAAAeP4ixAAAACXBIWXMAAAsTAAALEwEAmpwYAAADvElEQVR4nO1Z3WtUVxC/jfUtmsy5roovYgmKIIj4oKKlVpM7s7FSaBU/3vwPRPx4XB9EH/sRrR9JvDM3mkq0IKVQ+lToB5FCQUUfLBgFo4iiIFEx8WPLnN00UTfuPbs3d1PZgXlYdu+Z32/mN+fOOet5datb3epWt7rVrW7/Y/v1kw8N0yZg7ALGq4bxvmF6ZYTyibiuxXjfCF0xQp0mDL7UmIlyAMZthvFmYqDj+w2Q7JbqGfRtnmazkz6B/OvVwhNeLtdQMQ8jdKzmJGTU8bsKSeAXtQdPr7kv+Lm7pGrTE/l3S4wGFFtsHiDUXnPQMiGZwEVWx2sOWBLoFRD8q/aAqaQD44XYRBpPfzbLO758ut/VOs8ItoJQBzANpQ+ahjS2H9J6xaKYLLZqbHbvujmGqS81IoxnNGZFYJt78GNdAIRuG8ZhEBw0jN+D0Br7g7z3gWE8lAKJQxorFqYSc9TRMosfsbOPJTOJlWE8Y0m4YBq1sg+Mf9DzvEzYPncyegaYhkbl5IqpUDqXYGF2tT4HTIcTJyLUUTEmLaVjwF6bsShoS15a2FqoRgWYbBM5ZQ0HNVhha06WiK9bbGGycMekO4FTQMYXdqS2Iz6+TLAaL+0clcs1aAxHTMOq9TuuQWfIet9KQPBeUkSA6a6u2dhNGednixVx1WMeOJstNvz5BIn8UMXA2utpx7uevUHoG7u7RMFSHa0TkNV1iNqWFJKD37rJil6B4Cq7BSswx+w9niXZhV7C5vfgIhB84pjUr8dWyOUa3MngLYhoa9VDXHFIBQm2G8YfrcetBONXJc/yWiLDdDop3Tsm5lpjZ/tiP8quA6aojBRPmZBWls1QTYgI7rJ3ZkL/mKhtxbt+G7vU6RHAe3rZB4L9zV3t84HxUVH3a0DwrBG8VOruYEoRAaGDTULL9EbRcLBDj7BmrDq/6KWg3YpDWumHuHb8zjqliOjVDghKDMkNzu2jzJQlor0wMwpaQHD/hO8xpj/nRBsXgNC5iqQFjE9T6pMHPgefAuOBEpXobz6lfUN/v/HdiENF8HJKRPIQ4l4QOvl2NfCm7aG3qzQQn0jc01kCbsGO7Uw/Fe8ERvTzzM6NLYbxYckTYRzLREGL8yhdoTf2UUbPH/pmB8FV+jdCgRxd1P9jtE/GVeN5U/eGjzwX0xdUKtIS3KOJKwyLOHq++bmJNyyHMKA3Zq+dTiT+I8O0zwg+S0tmZkLHZ8C026t2Iq01Eb8HF3lJWLlAU33995EI/jFhIKbfJnd9/D3OIv8CqtwTGaSLUnQAAAAASUVORK5CYII=">
                                    </div>
                                </button>
                                <button  v-if="seat.seats.seatTypeId == 2 && seat.status == 1 && seat.customerId != this.model.auth" type="button"  class="btn btn-none border-0 shadow-none col-12">
                                    <div class="col-12 text-center mb-5">
                                        <img style="width: 1.5vmax;" src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADIAAAAyCAYAAAAeP4ixAAAACXBIWXMAAAsTAAALEwEAmpwYAAADu0lEQVR4nO1Zz4sUVxDuNXpTdF7N6LIXSVhcBCFIDjFEwfgjRC9CEkjizf9AJJqrh6DHRDf+ihIwRCNJhCCCeBISxRBMUNntqp7tqt6Jo4hLhLAqatSWejOrq447/Xp6eyZhCuow9OtX9b3vq9f13nhe17rWta51rWtd69p/2M6cmWkYPwTBQ8A4DIJjwPgIhOJM3M6FYyA0BIIHDeMHGjNTDMXQ/wSYRjNLOjE4igpCH7WOII5f0dXJHYA864bxay+OZ6TGYZj2txsETIAR3JsOROi/3+7k4UXf4C6pdtSENHFG0dwS4yiGwfq2Jy0vk5j/bnJZMR3oXCCYvFaM4O/tThheLq/fEgOZTVT0LlyYBRXsMxysAaFBIzSe/+qTxhyEkFZrLpqTza0Vm8+XF4DQDzmu/DGNmSrZIgcrdALDdBWE7gFj1TB+X2BabgfEcY8R3JlDHezUWIlyerGPon1NJt9je5847plWZhiPWRAuOU1YsxeeedHzvFI01DsdNWOExifk5JpTjTqHYIWQ3raBBL+aBkYGU+ekVDqu2tHaivlrM2eEgzU6d6qc6kWUPCBj1QarYF/mjFSwry4r95zsTuD20gPbUtt+DB9mBoLxoe2j4niGxnB8/56iv+YadE7Vh3qd3MhMVkLXdc7ecrmUYhGqznpUL0S0riYB/DlDaR1P27DaGtGKdz57M+3SoPMkeF1b65bZYORC6C+pFTrtdmTjUSHy37JbsCbmFphuFdlf5GVsIDhgmG47LuqXT2ewBeYGBgSvFKPg45abuHqTCowbjdAJ9aRMAOMXDc/ySpEROpKh7l10HvQGwWIIaZVh/LbJ2O9M5C9LQHH+QApMW/TOzAiVjQRvTjU2MdX5sYA37GUf0/leGV4Igv/UQS0HoR9B8FKju4NOA7JjblReqjeKJsRNeoSFJ/qn03opqFuxSggiXDl5Z+00IBuA8XDTcYxV+5HsVCBaC6WRkX5g3D7Fd+zcglF6FYR+SiUtw3gnF1aY/oYI3wGhzxs8Oz9Phhcapj+ee3bfhZHLOclLfRsIfdMAyGgxKi9tIDVxYCTZ6SwLt8nWdyYjeLJ+J3Bff5f+UunRzYYnwiRWGhnqT9FKp/LZ5T9L9vzBuFE/yPo3goIzjBdr/8fQuUnj/51fCV7zXKz2gcqDFdxaWzja/eR8w3iqWAnfKET03uTey0S02UtjIPSZEbybY73EjbyWA36aCsRTMDjQbiAgONASiEnMTBmo0+f/PwLBs1Po95fpnB8Ef00yyWOYc8fu6UUDkgAAAABJRU5ErkJggg==">
                                    </div>
                                </button>
                                <button v-if="seat.seats.seatTypeId == 2 && seat.status == 2 && seat.customerId == this.model.auth" type="button" disabled class="btn btn-none border-0 shadow-none col-12">
                                    <div class="col-12 text-center mb-5">
                                        <img style="width: 1.5vmax;" src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADIAAAAyCAYAAAAeP4ixAAAACXBIWXMAAAsTAAALEwEAmpwYAAADvElEQVR4nO1Z3WtUVxC/jfUtmsy5roovYgmKIIj4oKKlVpM7s7FSaBU/3vwPRPx4XB9EH/sRrR9JvDM3mkq0IKVQ+lToB5FCQUUfLBgFo4iiIFEx8WPLnN00UTfuPbs3d1PZgXlYdu+Z32/mN+fOOet5datb3epWt7rVrW7/Y/v1kw8N0yZg7ALGq4bxvmF6ZYTyibiuxXjfCF0xQp0mDL7UmIlyAMZthvFmYqDj+w2Q7JbqGfRtnmazkz6B/OvVwhNeLtdQMQ8jdKzmJGTU8bsKSeAXtQdPr7kv+Lm7pGrTE/l3S4wGFFtsHiDUXnPQMiGZwEVWx2sOWBLoFRD8q/aAqaQD44XYRBpPfzbLO758ut/VOs8ItoJQBzANpQ+ahjS2H9J6xaKYLLZqbHbvujmGqS81IoxnNGZFYJt78GNdAIRuG8ZhEBw0jN+D0Br7g7z3gWE8lAKJQxorFqYSc9TRMosfsbOPJTOJlWE8Y0m4YBq1sg+Mf9DzvEzYPncyegaYhkbl5IqpUDqXYGF2tT4HTIcTJyLUUTEmLaVjwF6bsShoS15a2FqoRgWYbBM5ZQ0HNVhha06WiK9bbGGycMekO4FTQMYXdqS2Iz6+TLAaL+0clcs1aAxHTMOq9TuuQWfIet9KQPBeUkSA6a6u2dhNGednixVx1WMeOJstNvz5BIn8UMXA2utpx7uevUHoG7u7RMFSHa0TkNV1iNqWFJKD37rJil6B4Cq7BSswx+w9niXZhV7C5vfgIhB84pjUr8dWyOUa3MngLYhoa9VDXHFIBQm2G8YfrcetBONXJc/yWiLDdDop3Tsm5lpjZ/tiP8quA6aojBRPmZBWls1QTYgI7rJ3ZkL/mKhtxbt+G7vU6RHAe3rZB4L9zV3t84HxUVH3a0DwrBG8VOruYEoRAaGDTULL9EbRcLBDj7BmrDq/6KWg3YpDWumHuHb8zjqliOjVDghKDMkNzu2jzJQlor0wMwpaQHD/hO8xpj/nRBsXgNC5iqQFjE9T6pMHPgefAuOBEpXobz6lfUN/v/HdiENF8HJKRPIQ4l4QOvl2NfCm7aG3qzQQn0jc01kCbsGO7Uw/Fe8ERvTzzM6NLYbxYckTYRzLREGL8yhdoTf2UUbPH/pmB8FV+jdCgRxd1P9jtE/GVeN5U/eGjzwX0xdUKtIS3KOJKwyLOHq++bmJNyyHMKA3Zq+dTiT+I8O0zwg+S0tmZkLHZ8C026t2Iq01Eb8HF3lJWLlAU33995EI/jFhIKbfJnd9/D3OIv8CqtwTGaSLUnQAAAAASUVORK5CYII=">
                                    </div>
                                </button>
                                <button v-if="seat.seats.seatTypeId == 2 && seat.status == 2 && seat.customerId != this.model.auth" type="button" disabled class="btn btn-none border-0 shadow-none col-12">
                                    <div class="col-12 text-center mb-5">
                                        <img style="width: 1.5vmax;" src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADIAAAAyCAYAAAAeP4ixAAAACXBIWXMAAAsTAAALEwEAmpwYAAADpElEQVR4nO2ZSWsUURDH2+0TaDJVrcEFMQiCiAcVFdxRL4IKLje/gQSXqwcxR5e4K4LihguICOJBolM1RkVBRQ8GjAGjiKIgUXG6nj6pnklMdOL06+lZlCl4h5npflW/96/qrvfG8+pWt7rVrW51q1vd/l2z7d5IycBaYTgujM+E4b0Q/jCMNomhcwnDe8P4VAiOCcMa9ZkohEnjBiHsTipoB7iXhv11JQPYC94IXZ1KA5g/gOCotd7w2CDCeLjaEOaXOgfjQRCsrnbw5ncYxlUxUqryNWGKg3RpbNHVYFhZ7aDN0DDLHEDwSM2CkEOtGML71Q7YDD3uRgax7TjGPvBGWW7yhfwlwtAmjL1VSKPe0HfaX6yxhDG145jIIAXhOhpThvFC5VIIzqvPWMEGjPN1AiF4LQRZIegRgnMB4bwQxnrDhKG1/EpAq/qKEtNvqeSNFMJDRWQ+oNepg3IqI6qE9Ya5xNQPUuyGgTfmwBugHDUjjL196eQaUyidi7MgjXNDR4z7y5BSbbFjUikdnZ3Nr9jS5NPKX5KbO0ZMWkRuzqAnTC9u8pMGsdzk50HcY9IngRs9Gm2p8/3Y9+TUwO86p86tPhxBsprrb5xX7p4/Ol8n7xIEeRsqnYYG93tzipyPceMKdWoIriSYWpfjNqxhjWjFu+69hWCvOs3S2OnaWpesBuOLbCY1LV8f+xyV/BGwPyf/HoG9jo4/27Q/xUvYLPvNQvDFUY09vybQAnOFIXhlMv76kpu4fJNqCDcahqu5EU0JYdhdcC+vEgnDmQTz3mVln9tbMFUyqUXCeKrIIp4OqHF20RWqBohhaMmdmUFn0JGa9bdrI0tdORXwnR72GcYOexPGC+En/V47W0N40TA8LnR2UFMgwrArm/Fn6ImiyfibdAtr+n4nuBEeCjKs1BQSSi0Y+GStMRBcJYwni15H0KMvyRoGgU57p2GyEO4Y8j1GkLG3UxMN4aVYqSUEXysCQ/BBOLVQCHcW+L3DPpww3jA8HHwPBtEVIXxSCZD82CYEJ/6ExG6toQIp2eWgSLTdWRIjLPi+JxPhNd2v66rr5zD1GD4W3BFGMXtn3GTXVjruyBUyvNY3e8D+HP0bIacEPNL/Y7ROBkCIpcZJkUHC9GJoqYwqqa3hwhHsG7C/uR7cxZmShuWDei/CzU4Q/TCE24XhWwXrxRYaYQwEW7xSO9Jqg1j2m0uC6FemiKNan/9/BAEe0hFBuqzzM1CUSX4CI/gkjtJHJ7IAAAAASUVORK5CYII=">
                                    </div>
                                </button>
                            </div>
                        </div>   
                            
                        <div class="row">
                            <div v-for="seat in model.tickets" :key="seat.id" class="col-2">
                                <button  @click="orderTicket(seat.id, this.model.auth)"  v-if="seat.seats.seatTypeId == 3 && seat.status == 0" type="button"  class="btn btn-none shadow-none col-12">
                                    <div class="col-12 text-center mb-5">
                                        <img style="width: 2.5vmax;" src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADwAAAA8CAYAAAA6/NlyAAAACXBIWXMAAAsTAAALEwEAmpwYAAAC8ElEQVR4nO2aPWgUQRiGV6OoJEZMpRhR/AkKGn/Bf0khYqFR0EpCsDKCAU0s/MPkCsEipdhYGbCRIAqigj9djDYiaUQQtREEFb0gGBX1kQ++k2G5bOZuZu82YR7YIrMf774vMzezO5MoCgQCgUAgEAhUGaAR2AnscrhWAjWG5jRtc9EUTwt8Bp0LXMcfw4b2sCfNv8AtoME17BTgHp4x9H3zQDy7BN6Tgqk0Awu7XQKfnYCBz7gEzk3AwLkQ2BbgkM6AXjH0fSNeD1oHLAawGXjq05Wh7ZMh8VrK8tMUW9C3AfV6fxbwOMOBHwEzVbNevZtZmv4vV8D8hB78DnRo3WLgZwYDi6dFqncMGE0YAfOkaGAcwd/AahW8m8HAd1SrWb0mcUMKRyxEu1S0L4OB+1Sry6I2H5WytgE9ZC9wTynvDFGJgdcA94GHZV7PgX4jcL9+QAyVqSdemlMLnGXS6uEaYLvDt+uyIkaXO+iJl6lpBu7E/U3ovBH2Au4cTzNwDnfyRmCbFcKrt6hE0VYPLx9DRuBnjlriZV9qgbNMCOxpSO/39T7tCfHSmloPk9IOSJYnrRzZIwROIsKO0MNV4AfwIbbH9g3onmy/4U9Au2wzqYfZwFFgY2wd7pwMgfPACn32Ft3CWat/1wKHgTY5/9K2qxM98Dl97kWjTYb0JeC10fYeWKi9/zVJMALeZTjwKtl4A/5Y1F5RjzcTat5KwSkLsV4V66WyyE7pOsva2+rxWkJNd2FPugN4Arwpcr0EtqrYJuDVGHVpXDuAGcBHi8AnjR6O6wzqRFf+UWolkY/8ccJKqDqXB9QBSxKuRq+J7DwNJKzPG7TG9FhrKyxHFV8shtDptEPGfM0BXsQ8yGTWrvdPxO59tgoNTI9N+WPRVomgMW8NutVbCHtE2w8Av2L+ZK6psRVemnDeNFI4iagGOgIvA3uNf8uQYW0yWDhvKgldFlqMbdH11r+NCiHnXoa/lrKCBgKBQCAQCAQid/4BnQc5hEvJvewAAAAASUVORK5CYII=">
                                    </div>
                                </button>
                                <button  @click="orderTicket(seat.id, this.model.auth)"  v-if="seat.seats.seatTypeId == 3 && seat.status == 1 && seat.customerId == this.model.auth" type="button"  class="btn btn-none shadow-none col-12">
                                    <div class="col-12 text-center mb-5">
                                        <img style="width: 2.5vmax;" src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADwAAAA8CAYAAAA6/NlyAAAACXBIWXMAAAsTAAALEwEAmpwYAAAD6UlEQVR4nO2aX4hUdRTHf2qhke3M+c0sFRqKmhRk/wwqzbaH9Z4zs2pB7UtI9FRBQWkP/SPXh6AHn0J6sGzvOXfsoZEoCAv8gy/r1kuELyGE+hIEGrUS2G6kG+fOzuw0Obt37tw73o3fF36wc/fHuefzO7+/53eNcXJycnJycnJyus6yFVqZ5/LjVnAwfinfbarDSxpGTw7coM+6sRn6xEMrEgPNfToEVvCQFZpOpuDpRiMKnk7EJtNVYPyi72PPdkc7bRZZwa+Tg62VWeBk7QLTUfU5Ni/4HiXtVJrAM9H2YgNbxrcWGjAIvRk/woJ7Fx4w7nXAUWWZntEZcMFEWH31vacjA15L1qdHQPDbzAMzjauvJpKmzaKilNY3L+jglzbbCvXpv1dWh28CxhNZBQbB46v8gWWhzQr1hb43sRSltL6xXBUreHu7CALjZWB8UevlfFxtGacyB8w4lT9UXqX2QPAlEPqzXQ/o98u3aaXD8xj8G0ZLG0IHGY9kD5i+Ult5pnvV13nqf2aA8VIEo7tqDuK+zAEL7qsFg3ZFqD9hOlnbrNCe7AHTnk72DKYT4Hzg3WeFvgGmYzHL9yAodWD9OzxAMI3Hsae+aFdODTjLSge4OrwEhB6Le3btD7x1rY4WRwfvjGtPfTEjI4tTA7bsvdLVeKvt2t6pw1rBd7sdw4UAX04NGJI5TEw0umGUFSJh30wnRguMO7refDCNNwF/150tnMoHtD29MZxhOWBJoksLPpnUfjqRwjilwyy1CENKGZDMTlrggMlF2LouTQk1Ak6C4C/NOTZg+gMEd/+/xjDjRcul5zTNFK4UB3fcAkwvFKT0UPM6HHXbazIOPFHwvbtm3v2opnByfvl+/X1rsPVmEO/ZPNNOvf+qQeNHCxuY8e3wvYzvzT6jq5bxfWD6qcm/n2HUu0OjbwV/nw/4fFaBIdh6jyberOCVCI3zYa1x6PP2deicAfFen98YjdS6DI30ElgzpTmhByI1DtOXM72B5wjc7jAnralYy3TKCp5tLcD4IwTephA4KD8MTGeuVS+Nkq/gFvMBLbWCFyJAvzYb4f/YGtOJrqur1F5KD/lzw+LZ/urA8tgv6K8OLM99MrSmXdHPH0yP1T5/jpNF9jZqnWYfdRY3UaRXFZbxtwhj5g3TQ8GBwZwV/KEF9oqu0aHfjK+2zDu/RoM+sPHG5im/XdH1z/RY+g2HpnobsAE+r88LQekpK/RXS0DO/OsDmjkNM62d477pUv0m4noovCwT2p8Xb9vsZxk42RL5sfp9U0fSZaHg4xONW7gKPhh5bPRIeu9V9099jQXq5OTk5OTk5ORkutc/H+IWmsAjGBIAAAAASUVORK5CYII=">
                                    </div>
                                </button>
                                <button  v-if="seat.seats.seatTypeId == 3 && seat.status == 1 && seat.customerId != this.model.auth" type="button"  class="btn btn-none border-0 shadow-none col-12">
                                    <div class="col-12 text-center mb-5">
                                        <img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADwAAAA8CAYAAAA6/NlyAAAACXBIWXMAAAsTAAALEwEAmpwYAAAD4klEQVR4nO2aTYwUVRDHGxGDSna3680oBAgEdQkHMHrwkxgPxOABPMCBA8GbKOoBOKAxAic9EA8evZhgvBhjPBgkUQkXXAwZEiRDV3UPVc1uQogJCOtB2ERtUz0fzE6YnZ6e7qEnef/kJbO9LzX1e6/qvdevxnGsrKysrKysrKzusyAIVpXEfwXY35K6hf4GJ4oWt4yePv2gPhvEZuzTjL8yM9Dx6YsuCH1thKJsGv7etK2fM7HJ+B8wfj82U4XBaKNokWH8MTvYersLnK1dI/ST+pya1w1paw5O5QkcgXivpQYG9j4cNWDD9EFqYMN4dPSA8agFTipg3Kkr4MjMcH213pEY8F6C0HvBMJ0tPDDTlPrqJFIULSqxN9m+obuX6WUIgjH996qZmYdB8FRRgUHwlzVhuDSeoCAYi31vP5ywN9narkpXvBXdZhAY/zaCe7XfeIhrjdBcAYHnJuTSmtheiG8D4+1uEVAOq8v1S7/tkRf/uIwb49ETPFE0YBD6QW1NMG1SX3uwfKPHu9meRpn2x8BMxwoHzHSs4dv+3v3xltPP3gZChwsHLHS4nzOD0w/whPhPG8aTRvDnNA2YzhvG4y1gxuPxCwTTVCqbjCc1lHMDLrLyAY6ixS7T5rTvruVa9clOR0uXLz2V1p764kTRA7kBA3vvZXAS+qgJC0IfD5zHTO/mBmwyeZnAW60wTLBDZO2b05dRwe0DHz6Yptry7rcBgecM47b8crjAssCSSUjTG1mdpzNqc5pmuc2wyekGpLiLFlvgyM6w2JCOsslVug6MCIJ32p5Pj8BJi/pqwMhaEGiemZ1q9aFS6O/SG5j5+zC9M/LAwHRVr6AaJZ9tesnu1vAl9WV5EJTjsz3TPv2sz4Dpi5EGNo37NCP05Xx/6HMQ/KNtYK5pddNlHgehvxYGZgqLCuzWaquN4PqEg/NZw8fuxT9G0Q4He4aW0JE4ZISODBNYQ1XfeZP0BcavGtHwXdcBZDpQL4kK7jVCv+oC0dkMo9fMGxD/eWCie/XLp/nPrbhaecQw3eg9Kf6eOrBeJXUwCJ4pCb41UCl1mALB9xeeXTrvVCpLUn9BuVpd9ti0v65b0wXCGbK63p8z3iwHwRN6/dTu4+PXLjyayLCWKgzTnwny5lDulB1+gVBlfhjjnXiPrkfBp/MHgq4ng65UloBQrScw025nyKr/3gTPNRap225Ir+vzeA3qqHLqWuO0/4BmIWmIdK8Y4myzEnE/pOlmhD5xQ+9F/RvEe9Mw/tvh45lmvakvxQW0EF9tVeGueM8mzo0hqRQGzzT9U19TgVpZWVlZWVlZWTmD639QVMVHxryNZAAAAABJRU5ErkJggg==">
                                    </div>
                                </button>
                                <button v-if="seat.seats.seatTypeId == 3 && seat.status == 2 && seat.status == this.model.auth" type="button" disabled class="btn btn-none border-0 shadow-none col-12">
                                    <div class="col-12 text-center mb-5">
                                        <img style="width: 2.5vmax;" src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADwAAAA8CAYAAAA6/NlyAAAACXBIWXMAAAsTAAALEwEAmpwYAAAD6UlEQVR4nO2aX4hUdRTHf2qhke3M+c0sFRqKmhRk/wwqzbaH9Z4zs2pB7UtI9FRBQWkP/SPXh6AHn0J6sGzvOXfsoZEoCAv8gy/r1kuELyGE+hIEGrUS2G6kG+fOzuw0Obt37tw73o3fF36wc/fHuefzO7+/53eNcXJycnJycnJyus6yFVqZ5/LjVnAwfinfbarDSxpGTw7coM+6sRn6xEMrEgPNfToEVvCQFZpOpuDpRiMKnk7EJtNVYPyi72PPdkc7bRZZwa+Tg62VWeBk7QLTUfU5Ni/4HiXtVJrAM9H2YgNbxrcWGjAIvRk/woJ7Fx4w7nXAUWWZntEZcMFEWH31vacjA15L1qdHQPDbzAMzjauvJpKmzaKilNY3L+jglzbbCvXpv1dWh28CxhNZBQbB46v8gWWhzQr1hb43sRSltL6xXBUreHu7CALjZWB8UevlfFxtGacyB8w4lT9UXqX2QPAlEPqzXQ/o98u3aaXD8xj8G0ZLG0IHGY9kD5i+Ult5pnvV13nqf2aA8VIEo7tqDuK+zAEL7qsFg3ZFqD9hOlnbrNCe7AHTnk72DKYT4Hzg3WeFvgGmYzHL9yAodWD9OzxAMI3Hsae+aFdODTjLSge4OrwEhB6Le3btD7x1rY4WRwfvjGtPfTEjI4tTA7bsvdLVeKvt2t6pw1rBd7sdw4UAX04NGJI5TEw0umGUFSJh30wnRguMO7refDCNNwF/150tnMoHtD29MZxhOWBJoksLPpnUfjqRwjilwyy1CENKGZDMTlrggMlF2LouTQk1Ak6C4C/NOTZg+gMEd/+/xjDjRcul5zTNFK4UB3fcAkwvFKT0UPM6HHXbazIOPFHwvbtm3v2opnByfvl+/X1rsPVmEO/ZPNNOvf+qQeNHCxuY8e3wvYzvzT6jq5bxfWD6qcm/n2HUu0OjbwV/nw/4fFaBIdh6jyberOCVCI3zYa1x6PP2deicAfFen98YjdS6DI30ElgzpTmhByI1DtOXM72B5wjc7jAnralYy3TKCp5tLcD4IwTephA4KD8MTGeuVS+Nkq/gFvMBLbWCFyJAvzYb4f/YGtOJrqur1F5KD/lzw+LZ/urA8tgv6K8OLM99MrSmXdHPH0yP1T5/jpNF9jZqnWYfdRY3UaRXFZbxtwhj5g3TQ8GBwZwV/KEF9oqu0aHfjK+2zDu/RoM+sPHG5im/XdH1z/RY+g2HpnobsAE+r88LQekpK/RXS0DO/OsDmjkNM62d477pUv0m4noovCwT2p8Xb9vsZxk42RL5sfp9U0fSZaHg4xONW7gKPhh5bPRIeu9V9099jQXq5OTk5OTk5ORkutc/H+IWmsAjGBIAAAAASUVORK5CYII=">
                                    </div>
                                </button>
                                <button v-if="seat.seats.seatTypeId == 3 && seat.status == 2 && seat.status != this.model.auth" type="button" disabled class="btn btn-none border-0 shadow-none col-12">
                                    <div class="col-12 text-center mb-5">
                                        <img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADwAAAA8CAYAAAA6/NlyAAAACXBIWXMAAAsTAAALEwEAmpwYAAAD5klEQVR4nO2aTWhcVRTHX4wVP0okwcmc82ZsxbQRC1Xsws8gXYjYRdOFLlyUdtfYDxeti7aUNq7sQly4dCMoboxIF0WLjRLzzpmXQZKFICqUtnRRpFDtx6LJzL16y3kzk2QGJ/PmzXuTN3D/cOHlzXByfjnnfp0Tx7GysrKysrKyslpnmWIuXy7A64rcN6IOMwfPmimnf9nmjPOgvOvEpvhk/HwuPlDaNKgIvtKMJp4Bv9Zsy3McNhXhf5rhnPHzQ53BGqdPM34fH2xlrADHa1czXBSfIwMrD96K36kkgdEoxjcjA2vCk70GrAlPRI8w4Ye9Biw+W+CwUgV4p7IC9kaExVfF8LbTico0/LJmnEs9MIEvvoaCMsbpM547Wrehe/iaKQ4NBJ/7+Uc04U+pBSb40cxsfjjwtTg0IL7XHXg8d3R5uzKzT2CzCCqCe5pgIvjeXPYpRVBKG7D4ZAqwuWIP3lMMi80ywMxkQLaeb9Y0yKhL/vD2wCDhd2kD1oznxVbJyz0nvrZg+Vq2njutjcLRYBFj/DhtwOJTNbpHW2cD3nba2ds0w5m0AYtP7ZwZnHaAS5R7XjNe0AzTEceCYvyiBizPwQWCwI9mDy9IKicGnGYlAmymnP4y4Vjk+7Cf39LoqPk5tzXyXZhwzBjngcSANeGRGO6tp2qwmuB0x3OYsocTA1YxXCaClXIlDUPsEPH65rRllN3xjg8fBP5yhBmLncFCSZG7OzHgNMsCcywpjXviOk/HMYKUZnc8sQirhCog6V20yAIbG2G2KW1iWqBuKoI/FMPS8juGa6k/ael2QRkvS0OgdmY2v217SBfcd6UCs3of1gwHex5YEVyXEpTUo+REJUX2csF9NQD3IBOc7T04JM/VbfOzngbW1XqaIvi84Q/xqSK8sSoL/pLuppkffFwR3l0TWBFeTSuwmXWfNOw+EzIon1RSu3nzTzFekSvaB60NwmR1nkx2FdiDjNx5QwEzflkF/nYNjmOVlijBhCYoBAtE4yD8vTZvyl72JUXw5/9+L4FR9rMvmnl8VBH8HSL991WDMt1oRzOwJjzQUSu1m9KM77fIwAUz72yI/AvMTGajoeGnm45iLu90Wc3q54rhluHMiJSf6nz8IftYKMPSqlAM/7ROITyeOGWDX5pxvgF2SfZo+VwxnK1fxOBmKGhJDUVwKcRCtrcboHW+0aZBTfhLFXZREeyS97IGNXY5Za0xq/6BZm3DnBlp3m+SOlSlE7EekummGD4qs/uK/KwJ9ivCfxuCwbV+U1uqNNCyO2tl0dIs7gg9N7qkUsF9YaV0m90ZCdTKysrKysrKysrpXPcBqXU0zAX2I9kAAAAASUVORK5CYII=">
                                    </div>
                                </button>
                            </div>
                                

                        </div>

                    </div>

                </div>


            </div>
            <div  v-if="model.schedule.room.roomTypeId == 2" class="col-7 mt-5">
                <div class="row screen mb-5">
                    <img src="../assets/image/bg-screen.png" class="object-fit: cover; width: 100%;" alt="">
                </div>
                <div class="row seat d-flex col-12 " style="margin-top: 1vmax;">
                    <div class="col-1">
                        <div class="row">
                            <div class="col-12 text-center  fw-bolder fs-5" style="height: 2.4vmax;">
                            </div>
                            <div class="col-12 text-center text-secondary fw-bolder fs-5" style="height: 4.8vmax;">
                                A
                            </div>
                            <div class="col-12 text-center text-secondary fw-bolder fs-5" style="height: 4.8vmax;">
                                B
                            </div>
                            <div class="col-12 text-center text-secondary fw-bolder fs-5" style="height: 4.8vmax;">
                                C
                            </div>
                            <div class="col-12 text-center text-secondary fw-bolder fs-5" style="height: 4.8vmax;">
                                D
                            </div>
                        </div>
                    </div>
                    <div class="col-11">
                        <div class="row mb-3">
                            <div class="col-2 text-center text-secondary fw-bolder fs-5">
                                1
                            </div>
                            <div class="col-2 text-center text-secondary fw-bolder fs-5">
                                2
                            </div>
                            <div class="col-2 text-center text-secondary fw-bolder fs-5">
                                3
                            </div>
                            <div class="col-2 text-center text-secondary fw-bolder fs-5">
                                4
                            </div>
                            <div class="col-2 text-center text-secondary fw-bolder fs-5">
                                5
                            </div>
                            <div class="col-2 text-center text-secondary fw-bolder fs-5">
                                6
                            </div>
                        </div>
                        <div class="row">
                            <div v-for="seat in model.tickets" :key="seat.id" class="col-2">
                                <button  @click="orderTicket(seat.id, this.model.auth)" v-if=" seat.status == 0" type="button" class="btn btn-none shadow-none col-12">
                                    <div class="col-12 text-center mb-5">
                                        <font-awesome-icon :icon="['fas', 'couch']" size="2xl" style="color: white;" />
                                    </div>
                                </button>
                                <button @click="orderTicket(seat.id, this.model.auth)" v-if=" seat.status == 1 && seat.customerId == this.model.auth" type="button"  class="btn btn-none shadow-none col-12">
                                    <div class="col-12 text-center mb-5">
                                        <font-awesome-icon :icon="['fas', 'couch']" size="2xl" style="color: rgb(64, 192, 87);" />
                                    </div>
                                </button>
                                <button v-if=" seat.status == 1 && seat.customerId != this.model.auth" type="button" disabled  class="btn btn-none border-0 shadow-none col-12">
                                    <div class="col-12 text-center mb-5">
                                        <font-awesome-icon :icon="['fas', 'couch']" size="2xl" style="color: rgb(19, 222, 216);" />
                                    </div>
                                </button>
                                <button v-if="seat.status == 2 && seat.customerId == this.model.auth" disabled class="btn btn-none border-0 shadow-none col-12">
                                    <div class="col-12 text-center mb-5">
                                        <font-awesome-icon :icon="['fas', 'couch']" size="2xl"  style="color: rgb(64, 192, 87);" />
                                    </div>
                                </button>
                                <button v-if="seat.status == 2 && seat.customerId != this.model.auth" disabled class="btn btn-none border-0 shadow-none col-12">
                                    <div class="col-12 text-center mb-5">
                                        <font-awesome-icon :icon="['fas', 'couch']" size="2xl"  style="color: rgb(252, 196, 25);" />
                                    </div>
                                </button>
                            </div>
                        </div>
                    </div>

                </div>


            </div>
            <div class="col-5">

                <div class="row content mt-3 mb-3 ">
                    <div class="row  mb-3">
                        <RouterLink :to="'/movieDetail/' + model.schedule.movieId" class="text-decoration-none mt-3">
                            <span class="border rounded-pill text-light text-center px-3 py-2 fs-5" style="cursor: pointer;">
                                <font-awesome-icon :icon="['fas', 'backward']" style="color: #ffffff;" />  Back 
                            </span>
                        </RouterLink>
                    </div>
                    <div class="row" >
                        <div class="col-6 hide-scrollbar" style="height: 30vmax; overflow-x: hidden; overflow-y: scroll;">
                            <div class="text-light fs-2 mb-3 fw-bolder">
                                {{model.schedule.movie.movieName}}
                            </div>
                            <div class="text-light fs-4 mb-5 fw-bolder">
                                {{model.schedule.room.roomName}} - <b v-if="model.schedule.room.roomTypeId == 1">ECONOMY CLASS</b><b v-if="model.schedule.room.roomTypeId == 2">GOLD CLASS</b>
                            </div>
                            <div class="text-light fs-4 mb-3 fw-bolder">
                                <span class="text-danger">Date: </span>{{ model.schedule.scheduleDate}}
                            </div>
                            <div class="text-light fs-5 mb-2 fw-bolder">
                                <span class="text-danger">Start time: </span>{{model.schedule.startTime}}
                            </div>
                            <div class="text-light fs-5 fw-bolder mb-5">
                                <span class="text-danger">End time: </span>{{model.schedule.endTime}}
                            </div>

                            <div v-for="seat in model.tickets" class="text-light fs-5 fw-bolder mb-2">
                                <span v-if="seat.status == 1 && seat.customerId == this.model.auth" class="text-danger">Seat: 
                                    <b class="text-light" v-if="seat.seats.row == 1">A{{ seat.seats.column }}</b>
                                    <b class="text-light" v-if="seat.seats.row == 2">B{{ seat.seats.column }}</b>
                                    <b class="text-light" v-if="seat.seats.row == 3">C{{ seat.seats.column }}</b>
                                    <b class="text-light" v-if="seat.seats.row == 4">D{{ seat.seats.column }}</b>
                                    <b class="text-light" v-if="seat.seats.row == 5">E{{ seat.seats.column }}</b>
                                    <b class="text-light" v-if="seat.seats.row == 6">F{{ seat.seats.column }}</b>
                                </span>
                                <div v-if="seat.status == 1 && seat.customerId == this.model.auth" class="text-light fs-5 fw-bolder mb-3">
                                    <span class="text-danger">Price: <b class="text-light">{{seat.finalPrice}} VND</b></span>
                                </div>
                            </div>
                            
                            <div ref="totalPrice" class="text-light fs-5 fw-bolder mt-5 mb-3">
                                <span class="text-danger fs-4">Total price: <b class="text-light">{{ model.total }} VND</b> </span>
                            </div>

                        </div>
                        <div class="col-6">
                            <img class="col-12 border rounded-3 border-0 " :src="model.schedule.movie.poster" alt="" style="object-fit: cover;height: 30vmax; width: 20vmax;">
                        </div>
                    </div>

                </div>
                <div class="d-inline">
                        <button type="button" @click="payment()" class="btn btn-danger shadow-none mx-5" :class="{ disable: this.model.total === 0 }"name="redirect"><font-awesome-icon :icon="['fas', 'credit-card']" style="color: #eceff4;" /> Payment</button>
                </div>

            </div>
        </div>
        

        <div class="row d-inline mx-3">
            <div class="row mt-3 mx-2 d-inline">
                <div class="d-inline" style="background-color: white; width: 0.5vmax; height: 1.2vmax"></div>
                <div class="d-inline text-light">Available seat</div>
            </div>

            <div class="row mt-3 mx-2 d-inline">
                <div class="d-inline" style="background-color: #40C057; width: 0.5vmax; height: 1.2vmax"></div>
                <div class="d-inline text-light">Reserved seat</div>
            </div>

            <div class="row mt-3 mx-2 d-inline">
                <div class="d-inline" style="background-color: #13DED8; width: 0.5vmax; height: 1.2vmax"></div>
                <div class="d-inline text-light">Seats are being taken by someone else</div>
            </div>

            <div class="row mt-3 mx-2 d-inline">
                <div class="d-inline" style="background-color: #FCC419; width: 0.5vmax; height: 1.2vmax"></div>
                <div class="d-inline text-light">Reserved seat by someone else</div>
            </div>
        </div>

        <div v-if="model.schedule.room.roomTypeId == 1" class="row d-inline mt-3">
            <div class="row mt-3 mx-2 d-inline">
                <div class="d-inline text-center mb-5"><img style="width: 1.5vmax;" src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAB4AAAAeCAYAAAA7MK6iAAAACXBIWXMAAAsTAAALEwEAmpwYAAAAr0lEQVR4nO2QQQrCMBBFc4EWdO+6Z5FuCsVLSsE72Eu4rt0q6AWeBFIRaWxnmkKlecsh89/kGxNZLcAOqIAncuzOCcg00hvTudssidj+NBRHiVhTr4+HRByUKP5VdQIUwGVCww1Q2qzRVX8csHEBGulWIsqBFrgCezc7KMSlL68X9+B9tZulCnHiy+vle9s3H2Iob/liLf8nDo2J4o71Vm0CM0ZcA+cZxPUcuZFl8wJRIS97SX64DQAAAABJRU5ErkJggg=="></div>
                <div class="d-inline text-light">Normal seat</div>
            </div>

            <div class="row mt-3 mx-2 d-inline">
                <div class="d-inline text-center mb-5"><img style="width: 1.5vmax;" class="col-6 mx-auto" src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADIAAAAyCAYAAAAeP4ixAAAACXBIWXMAAAsTAAALEwEAmpwYAAAC3klEQVR4nO2ZS2xNQRjH+2AtoYIGi6ZRUY+VhJSVakKIRyXUVoSdZ1KxsusOVeq5IPFohERiZWHhkXhtPBMb9SoRxOaqaNGffPK/nFztvWfmnnvuIee3anpmvu/7z3wz883cioqUlJSUlJSUlH8XYBSwBjgBPAE+AENEh9kym4+B40Cr+YxaRBvwgvh5DqyNQkC1RqfcHAOqihFyhOTQ7StiNcljhU9KlWNNFKLXYnMRspTk0uIi5CjJpdtFyF2Sy20XITXAaKAWaAa6gEwZgs7I9yLFYjHVhBYygrgJwPkYRfSYT99gF8rAG2AA6APOAQv0vRLoiEFEh/kKE9NwddThAsYPqV1liWemRz5CxxQUUqjD745qP7FEayaTTSfXmLJT50KT+h0kerq8Y9JUunBWzhYTPc2y7R6TFpELfXJm22HU1Mq2e0zaCVz4biW16rEfRIfZqpZt8+HCgAl56+F0nEbuPdHxTjbHe/Tt88lHY4mcXiI6LhZRsP5aI00ed+9OOZ2j0rpYngEzZfOAY1+LfX52C+507PwZmOZVPuSvLBqAfsdY9gcNVHmIeQ2sK7qI+1OkLgPqgKnArZAzsW/Yu7xNEXCG8mD11WaVP4XWyWlgXpgRihsb3XrgAfBNZ9TLkRq7THUcPAVO6b6xHZgb+LYDWAXs1YPgteCZlSQhj4ApwDZgj3L9Ts7DnKVaO7AJmCVRiRNyFWjUE2mYtNsI7EqikGz6TAbuFSjrW3XWffIR8iUeLZwExuakVfCsatRsBOvBQRchD4mP6Xrdz2VIF7jc3avXRUjY21mxvAImBUqkj8D9wPc27Wx/3whDCqn3KKV9sINtvf62BwUTNQbYDXzVLwEbAu3tjKkLLURibG8vNZdVX7UAs/UwaKm0HJgBrAS2BNpvdRIRENOukSklF5Q+gzn/v6Kn237FsNNLRECMjVi5aShKREBMXpJu/78UcjOPn+sltn8jjJGfT8zJxA5Aeb8AAAAASUVORK5CYII="></div>
                <div class="d-inline text-light">Vip seat</div>
            </div>

            <div class="row mt-3 mx-2 d-inline">
                <div class="d-inline text-center mb-5"><img style="width: 2.5 vmax;" src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADwAAAA8CAYAAAA6/NlyAAAACXBIWXMAAAsTAAALEwEAmpwYAAAC8ElEQVR4nO2aPWgUQRiGV6OoJEZMpRhR/AkKGn/Bf0khYqFR0EpCsDKCAU0s/MPkCsEipdhYGbCRIAqigj9djDYiaUQQtREEFb0gGBX1kQ++k2G5bOZuZu82YR7YIrMf774vMzezO5MoCgQCgUAgEAhUGaAR2AnscrhWAjWG5jRtc9EUTwt8Bp0LXMcfw4b2sCfNv8AtoME17BTgHp4x9H3zQDy7BN6Tgqk0Awu7XQKfnYCBz7gEzk3AwLkQ2BbgkM6AXjH0fSNeD1oHLAawGXjq05Wh7ZMh8VrK8tMUW9C3AfV6fxbwOMOBHwEzVbNevZtZmv4vV8D8hB78DnRo3WLgZwYDi6dFqncMGE0YAfOkaGAcwd/AahW8m8HAd1SrWb0mcUMKRyxEu1S0L4OB+1Sry6I2H5WytgE9ZC9wTynvDFGJgdcA94GHZV7PgX4jcL9+QAyVqSdemlMLnGXS6uEaYLvDt+uyIkaXO+iJl6lpBu7E/U3ovBH2Au4cTzNwDnfyRmCbFcKrt6hE0VYPLx9DRuBnjlriZV9qgbNMCOxpSO/39T7tCfHSmloPk9IOSJYnrRzZIwROIsKO0MNV4AfwIbbH9g3onmy/4U9Au2wzqYfZwFFgY2wd7pwMgfPACn32Ft3CWat/1wKHgTY5/9K2qxM98Dl97kWjTYb0JeC10fYeWKi9/zVJMALeZTjwKtl4A/5Y1F5RjzcTat5KwSkLsV4V66WyyE7pOsva2+rxWkJNd2FPugN4Arwpcr0EtqrYJuDVGHVpXDuAGcBHi8AnjR6O6wzqRFf+UWolkY/8ccJKqDqXB9QBSxKuRq+J7DwNJKzPG7TG9FhrKyxHFV8shtDptEPGfM0BXsQ8yGTWrvdPxO59tgoNTI9N+WPRVomgMW8NutVbCHtE2w8Av2L+ZK6psRVemnDeNFI4iagGOgIvA3uNf8uQYW0yWDhvKgldFlqMbdH11r+NCiHnXoa/lrKCBgKBQCAQCAQid/4BnQc5hEvJvewAAAAASUVORK5CYII="></div>
                <div class="d-inline text-light">Couple seat</div>
            </div>
        </div>
        <div v-if="model.schedule.room.roomTypeId == 2" class="row d-inline mt-3">
            <div class="row mt-3 mx-2 d-inline">
                <div class="d-inline text-center mb-5">
                    <font-awesome-icon :icon="['fas', 'couch']" size="2xl" />
                </div>
                <div class="d-inline text-light">Gold seat</div>
            </div>
        </div>
       
</template>

<script>
    import axios from 'axios';
    import { RouterLink } from 'vue-router';
  import * as signalR from "@aspnet/signalr";

    export default {
        name: 'BookingTicketView',
        data() {
            return {
                model: {
                    tickets: [],
                    schedule: {
                        id: '',
                        scheduleDate: '',
                        startTime: '',
                        endTime: '',
                        movie: {
                            id: '',
                            movieName: '',
                            poster: '',
                        },
                        room: {
                            roomTypeId: '',
                            id: '',
                            roomName: '',
                        }
                    },
                    total : 0,
                    baseUrl: 'https://localhost:7071',
                    auth: null,
                },
                connection: null,
            }
        },
        mounted() {
            this.scheduleId = this.$route.params.id;
            this.getTickets(this.$route.params.id);
            this.getSchedule(this.$route.params.id);
            // setInterval(() => {
            //     this.model.total = 0;
            //     this.getTickets(this.$route.params.id);
            // }, 5000); 
            // this.bookingTicket();
        },
        created(){
            this.isAuth();
            this.checkUrlParams();
            this.initSignalRConnection();
        },
        methods: {
            initSignalRConnection() {
                this.connection = new signalR.HubConnectionBuilder()
                    .withUrl("https://localhost:7071/bookticketHub")
                    .build();

                this.connection.start().then(() => {
                    console.log("Connected to SignalR Hub");
                    this.listenForBookTicket();
                    this.listenForOderTicket();
                }).catch((error) => {
                    console.error("Error connecting to SignalR Hub: ", error);
                });
            },
            listenForOderTicket() {
                console.log("Listening for order");
                this.connection.on("orderTicket", () => {
                    this.model.total = 0;
                    this.getTickets(this.$route.params.id);
                });
            },
            listenForBookTicket() {
                console.log("Listening for bookingTicket");
                this.connection.on("bookingTicket", () => {
                    this.model.total = 0;
                    this.getTickets(this.$route.params.id);
                });
            },
            isAuth() {
                if(localStorage.getItem('token_cus') == null && localStorage.getItem('role_cus') != 'Customer'){
                    this.$router.push('/login');
                }else if(localStorage.getItem('role_cus') == 'Customer' && localStorage.getItem('token_cus') != null){
                    this.model.auth = localStorage.getItem('id_cus');
                }
                console.log('akdah',this.model.auth);
            },
            async getTickets(scheduleId) {
                console.log('abccdc',scheduleId);
                try {
                    const response = await axios.get(`https://localhost:7071/api/Tickets/get-tickets-by-schedule?scheduleId=${scheduleId}`);
                    this.model.tickets = response.data;
                    console.log('res', response);

                    if (this.model.tickets.length > 0) {
                        this.model.total = 0; // Reset total before calculating
                        this.model.tickets.forEach(ticket => {
                            if (ticket.status == 1 && ticket.customerId == this.model.auth) {
                                this.model.total += ticket.finalPrice;
                            }
                        });
                    }

                    console.log(this.model.total);
                } catch (error) {
                    console.error('Error fetching tickets:', error);
                }
            },
            async getSchedule(scheduleId) {
                await axios.get(`https://localhost:7071/api/Schedules/get-schedule-with-detail?scheduleId=${scheduleId}`).then(response => {
                console.log('hahahaah',response.data);
                this.model.schedule = response.data;
                this.model.schedule.movie.poster = this.model.baseUrl + this.model.schedule.movie.poster;
                console.log(this.model.schedule.movie.poster);
                }).catch(error => {
                    console.error('Error fetching schedule:', error);
                });          
            },
            orderTicket(ticketId, cusId){
                axios.put(`https://localhost:7071/api/Tickets/${ticketId}?cusId=${cusId}`).then(response => {
                    this.$nextTick(() => {
                        this.model.total = 0;
                        this.getTickets(this.$route.params.id);
                    });
                    console.log(this.$route.params.id);
                }).catch(error => {
                    console.error('Error order ticket:', error);
                });
            },
            bookingTicket(){
                // this.$router.push({ name: 'PaymentView', params: { scheduleId: this.$route.params.id } });
                axios.put(`https://localhost:7071/api/Tickets/booking-tickets?cusId=${this.model.auth}`).then(response => {
                    console.log(response.data);
                     this.$router.push({ path: '/bookingTicket/' + this.$route.params.id});
                }).catch(error => {
                    console.error('Error booking ticket:', error);
                });
            },
            async sendEmail(){
                const validTickets = await this.model.tickets.filter(ticket => 
                    ticket.status == 1 && ticket.customerId == this.model.auth
                );
                const paymentData = {
                    // customerEmail: 'kiendoan8521349@gmail.com',
                    customerEmail: localStorage.getItem('email_cus'),
                    totalPrice: this.model.total,
                    tickets: JSON.parse(JSON.stringify(validTickets)),
                    schedule: JSON.parse(JSON.stringify(this.model.schedule))
                };
                console.log('asd', this.model.schedule);
                console.log('ticket',paymentData.tickets);
                console.log('schedule',paymentData.schedule);
                console.log('data',paymentData);
                await axios.post('https://localhost:7071/payment-success', paymentData).then(response => {
                    console.log(response.data);
                }).catch(error => {
                    console.error('Error send email:', error);
                });
                // await axios.post('https://localhost:7071/send-payment-success', paymentData).then(response => {
                //     console.log(response.data);
                // }).catch(error => {
                //     console.error('Error send email:', error);
                // });
                // await axios.post('https://localhost:7071/api/Email/SendPaymentSuccess', paymentData).then(response => {
                //     console.log(response.data);
                // }).catch(error => {
                //     console.error('Error send email:', error);
                // });
            },
            async checkUrlParams() {
                const urlParams = new URLSearchParams(window.location.search);
                const code = urlParams.get('code');
                const id = urlParams.get('id');
                const cancel = urlParams.get('cancel');
                const status = urlParams.get('status');
                const orderCode = urlParams.get('orderCode');

                if (code && id && cancel !== null && status && orderCode) {
                    if(cancel == 'false'){
                        console.log('Success');
                        await this.getTickets(this.$route.params.id);
                        await this.getSchedule(this.$route.params.id);
                        await this.sendEmail();
                        this.bookingTicket();
                    }else{
                        this.$router.push({ path: '/bookingTicket/' + this.$route.params.id});
                        console.log('Cancel');
                    }
                }
            },
            payment(){
                const validTickets = this.model.tickets.filter(ticket => 
                    ticket.status == 1 && ticket.customerId == this.model.auth
                );

                const paymentData = {
                    tickets: validTickets,
                    totalPrice: this.model.total,
                    scheduleId: parseInt(this.$route.params.id),
                };
                axios.post('https://localhost:7071/create-payment-link', paymentData)
                    .then(response => {
                        window.location.href = response.data.checkoutUrl;
                    })
                    .catch(error => {
                        console.error('Error booking ticket:', error);
                    });
            }
        },
    }

</script>

<style scoped>
.disable {
    opacity: 0.5; 
    pointer-events: none;
}
</style>