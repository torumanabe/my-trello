<template>
  <v-app>
    <v-card>
      <v-card-title>
        <h1 class="display-1">ログイン</h1>
      </v-card-title>
      <v-card-text>
        <v-form>
          <v-text-field prepend-icon="mdi-account-circle"  label="ユーザ名" />
          <v-text-field prepend-icon="mdi-lock" append-icon="mdi-eye-off" type="password" label="パスワード" />
          <v-card-actions>
            <v-btn class="info">ログイン</v-btn>
          </v-card-actions>
        </v-form>
      </v-card-text>
    </v-card>
  </v-app>
</template>