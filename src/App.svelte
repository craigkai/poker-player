<script lang="ts">
  import { onMount } from "svelte";
  import { supabase } from "./supabaseClient";
  import type { AuthSession } from "@supabase/supabase-js";
  import BestHands from "./components/BestHands.svelte";
  import Buyins from "./components/Buyins.svelte";
  import Blinds from "./components/Blinds.svelte";
  import {games} from "./lib/Store";

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

<div class="h-screen place-items-center bg-green-200">
  <div class="flex-row flex p-5">
    Game:
    <select class="form-control">
      <option>Last weeks game</option>
    </select>
  </div>

  <div class="flex flex-inline flex-row p-5">
    <div class="w-2/3 bg-gray-200 p-2 m-2">
      <Buyins {session} />
    </div>

    <div class="w-1/3 bg-blue-200 p-2 m-2">
      <Blinds />
      <BestHands {session} />
    </div>

  </div>

</div>

<style global lang="postcss">
  @tailwind utilities;
  @tailwind components;
  @tailwind base;
</style>
