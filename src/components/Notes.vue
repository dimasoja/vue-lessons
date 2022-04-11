 <template>
  <div class="notes">
      <div class="note" :class="{full: !grid}" v-for="(note, index) in notes" :key="index">
        <div class="note-header" :class="{ full: !grid}">
          <p>{{ note.title }}</p>
          <p style="cursor: pointer;" @click="removeNote(index )">x</p>
        </div>
        <div class="node-body">
          <p>{{ note.descr }}</p>
          <span>{{ note.date }}</span>
        </div>
      </div>
    </div>
</template>

<script>


export default {
  props: {
    notes: {
      type: Array,
      require: true
    },
    grid: {
     type: Boolean,
      require: true
    }
  },
  methods: {
    removeNote (index) {
      console.log(`Note id - ${index} removed`)
      this.$emit('remove', index)
    }
  }
}
</script>

<style lang="scss">
  .notes {
    display: flex;
    align-items: center;
    justify-content: space-between;
    flex-wrap: wrap;
    padding: 40px 0;
  }

  .note {
    width: 46%;
    padding: 18px 20px;
    margin-bottom: 20px;
    background-color: #ffffff;
    transition: all .25s cubic-bezier(.02, .01, .47, 1);
    box-shadow: 0 30px 30px rgba(0,0,0,.02);
    &:hover {
      box-shadow: 0 30px 30px rgba(0,0,0,.04);
      transform: translate(0, -6px);
      transition-delay: 0s !important;
    }
    &.full {
      width: 100%;
    }
  }
  .node-body {
    p {
      margin: 20px 0;
    }
    span {
      font-size: 14px;
      color: #999999;
    }
  }

  .note-header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    h1 {
      font-size: 22px;
    }
    p {
      color: #402caf;
      font-size: 22px;
    }
    svg {
      margin-right: 12px;
      color: #999999;
      &:last-child{
        margin-right: 0;
      }
      &.active {
        color: #402caf;
      }
    }

  }
</style>