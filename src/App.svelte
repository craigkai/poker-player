<script lang="ts">
  import { onMount } from "svelte";
  import { supabase } from "./supabaseClient";
  import type { AuthSession } from "@supabase/supabase-js";
  import BestHands from "./components/BestHands.svelte";
  import Buyins from "./components/Buyins.svelte";

  let session: AuthSession;

  onMount(() => {
    supabase.auth.getSession().then(({ data }) => {
      session = data.session;
    });

    supabase.auth.onAuthStateChange((_event, _session) => {
      session = _session;
    });
  });
</script>

<div class="container">
  Buy Ins
  <Buyins {session} />

  Best Hands
  <BestHands {session} />
</div>

<style global lang="postcss">
  @tailwind utilities;
  @tailwind components;
  @tailwind base;
</style>
