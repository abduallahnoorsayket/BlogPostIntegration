<template>
    <div>
        <MasterBlog>
            <template v-slot:blog>
                <main class="posts-listing col-lg-8">
                    <div class="container">
                        <div class="row">
                            <!-- post -->
                            <div class="post col-xl-5" v-for="comment in comments.slice(0,4)" v-bind:key="comment.id">
                                <div class="post-thumbnail"><a href="post.html"><img
                                        src="https://d19m59y37dris4.cloudfront.net/blog/1-2-1/img/blog-post-1.jpeg"
                                        alt="..." class="img-fluid"></a></div>
                                <div class="post-details">
                                    <div class="post-meta d-flex justify-content-between">
                                        <div class="date meta-last">20 May | 2016</div>
                                        <div class="category"><a href="#">Business</a></div>
                                    </div>
                                    <a href="#">
                                        <h3 class="h4"><router-link :to="{ name: 'Post', params:{id:comment.id}}">{{comment.title}}</router-link></h3></a>
                                    <p class="text-muted">{{comment.body}}</p>
                                    <footer class="post-footer d-flex align-items-center"><a href="#"
                                                                                             class="author d-flex align-items-center flex-wrap">
                                        <div class="avatar"><img
                                                src="https://d19m59y37dris4.cloudfront.net/blog/1-2-1/img/avatar-3.jpg"
                                                alt="..." class="img-fluid"></div>
                                        <div class="title"><span>John Doe</span></div>
                                    </a>
                                        <div class="date"><i class="icon-clock"></i> 2 months ago</div>
                                        <div class="comments meta-last"><i class="icon-comment"></i>12</div>
                                    </footer>
                                </div>
                            </div>

                        </div>
                        <!-- Pagination -->
                        <nav aria-label="Page navigation example">
                            <ul class="pagination pagination-template d-flex justify-content-center">
                                <li class="page-item"><a href="#" class="page-link"> <i
                                        class="fa fa-angle-left"></i></a>
                                </li>
                                <li class="page-item"><a href="#" class="page-link active">1</a></li>
                                <li class="page-item"><a href="#" class="page-link">2</a></li>
                                <li class="page-item"><a href="#" class="page-link">3</a></li>
                                <li class="page-item"><a href="#" class="page-link"> <i
                                        class="fa fa-angle-right"></i></a>
                                </li>
                            </ul>
                        </nav>
                    </div>
                </main>
                <Sidebar></Sidebar>

            </template>
        </MasterBlog>
    </div>
</template>

<script>

    import MasterBlog from "../layouts/MasterBlog";
    import Sidebar from "../layouts/partials/Sidebar";
    import axios from 'axios'

    export default {
        name: "Blog",
        components: {
            Sidebar,
            MasterBlog

        },
        data (){
            return {
                comments :'',
            }
        },
        mounted() {
            axios.get('https://jsonplaceholder.typicode.com/posts')
                .then(response =>this.comments = response.data)
        }
    }
</script>

<style scoped>

</style>