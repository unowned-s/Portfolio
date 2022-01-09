<template>
  <Layout>
    <div class="container">
      <div class="journal-hero">
        <h3 class="journal-header">
          a wise person once said...
        </h3>
      </div>
    </div>

    <g-link
      :to="item.node.path"
      v-for="item in $page.posts.edges"
      :key="item.node.id"
      class="journal-post"
    >
      <div class="container journal">
        <h2 class="journal-title">{{ item.node.title }}</h2>
        <small class="journal-date"
          >Published on: {{ item.node.date }}, {{ item.node.timeToRead }} min
          read</small
        >
        <p class="journal-excerpt">{{ item.node.excerpt }}</p>
      </div>
    </g-link>

    <div class="pagination">
      <Pager :info="$page.posts.pageInfo" />
    </div>
  </Layout>
</template>

<page-query>
query Journal($page: Int) {
	posts: allJournalPost(sortBy: "date", order: DESC, perPage: 3, page: $page, filter: { published: {eq: true}}) @paginate {
    pageInfo {
      totalPages
      currentPage
    }
    edges {
      node {
        id
        path
        title
        excerpt
        timeToRead
        date (format: "DD MMM, YYYY")
        published
      }
    }
  }
}
</page-query>

<script>
import { Pager } from "gridsome";
export default {
  components: {
    Pager
  }
};
</script>

<style scoped>
.container.journal {
  max-width: 900px;
}
.journal-hero {
  padding: 4rem 0;
  text-align: center;
  color: var(--color-base-1);
}
.journal-header {
  font-size: 3rem;
  font-weight: 700;
  padding: 0;
  margin: 0;
}
.journal-post {
  display: block;
  padding: 2rem 0;
  text-decoration: none;
  transition: background 0.5s ease;
}
.journal-post > * {
  transition: transform 0.5s ease;
}
.journal-post:hover {
  background-color: var(--color-base-1);
}
.journal-post:hover > * {
  transform: translateY(-1rem);
  /*transform: translateX(4rem);*/
}
.journal-post h1,
.journal-post h2 {
  margin: 0;
  padding: 0;
}
.journal-title {
  font-size: 2rem;
  color: var(--color-contrast);
}

.journal-date {
  font-size: 1rem;
  line-height: 3rem;
  color: var(--color-contrast-2);
}

.journal-excerpt {
  line-height: 1.5rem;
  color: var(--color-contrast-1);
}

.pagination {
  margin: 0 auto;
  max-width: 900px;
  display: table;
  align-items: center;
}
.pagination nav a {
  padding: 1rem;
  text-decoration: none;
  font-size: large;
}

@media (min-width: 560px) {
  .journal-post {
    padding: 3rem 0;
  }
}

@media (min-width: 860px) {
  .journal-post {
    padding: 5rem 0;
  }
}
</style>
