<template>
  <v-card color="#061422">
    <v-card-title>
      <span id="card-title">{{ $t('CardRoomSize.title') }}</span>
    </v-card-title>
    <v-card-text>
      <v-container>
        <v-row>
          <v-col cols="4">
            <v-text-field
              autofocus
              dark
              v-model="roomSize"
              :rules="[rules.required, rules.range]"
            >
            </v-text-field>
          </v-col>
        </v-row>
      </v-container>
    </v-card-text>
    <v-card-actions>
      <div class="flex-grow-1"></div>
      <v-btn
        dark
        depressed
        color="#43B581"
        @click="setRoomSize">{{ $t('CardRoomSize.next') }}</v-btn>
      <v-btn
        dark
        depressed
        color="#FF5252"
        @click="cancel">{{ $t('CardRoomSize.cancel') }}</v-btn>
    </v-card-actions>
  </v-card>
</template>

<script>
  export default {
    data() {
      return {
        roomSize: 2,
        rules: {
          required: value => !!value || 'Required.',
          range: value => (value >= 2 && value <= 20) || '2 - 20 Players',
        }
      }
    },
    methods: {
      setRoomSize() {
        // Pass room size to parent component
        this.$emit('setRoomSize', this.roomSize)
      },
      cancel() {
        this.$emit('cancel')
      }
    }
  }
</script>

<style scoped>
  #card-title {
    font-size: 16px;
    font-weight: 500;
    color: #FFFFFF;
    opacity: 0.9;
  }
</style>