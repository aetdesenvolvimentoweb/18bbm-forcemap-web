<script lang="ts">
  import { page } from "$app/state";
  import { House } from "lucide-svelte";

  let isNotFound = $derived(page.status === 404);
  let heading = $derived(
    isNotFound ? "Página não encontrada" : "Algo deu errado",
  );
  let description = $derived(
    isNotFound
      ? "A página que você procura não existe ou foi movida."
      : (page.error?.message ?? "Ocorreu um erro inesperado."),
  );
</script>

<section class="flex flex-1 items-center justify-center p-4 min-h-[60vh]">
  <div
    class="w-full max-w-md space-y-3 rounded-xl bg-base-100 p-6 text-center shadow-lg md:p-8"
  >
    <p class="text-6xl font-bold text-error">{page.status}</p>
    <h1 class="text-lg font-semibold">{heading}</h1>
    <p class="text-base-content/70 text-sm">{description}</p>
    <a href="/obm" class="btn btn-primary w-full mt-2">
      <House size={16} />
      Voltar ao início
    </a>
  </div>
</section>
