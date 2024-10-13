<script setup>
import TheHeader from './components/TheHeader.vue';
import {ref} from "vue";



// // // // // // // // // // // 
//          state             // 
// // // // // // // // // // // 

const titleOne = ref("Biodiversitet");
const titleTwo = ref("Oversvømmelser");
const titleThree = ref("Tørke og naturbrande");

const newsletter = ref({
    email: null
});

const registeredUser = ref([]);

const moreText = ref({
    section1: false,
    section2: false,
    section3: false
});

const throbber = ref(true);


// // // // // // // // // // // 
//          functions         // 
// // // // // // // // // // // 

// Kør throbber i 3 sekunder og derefter fjern den
setTimeout(() => throbber.value = false, 3000);

// Toggle section til og fra
function toggleText(section) {
    moreText.value[section] = !moreText.value[section];
}

function signUpNews() {
  //Alert bruger
  alert(`${newsletter.value.email} er nu registeret`)
  
  //Tilføj bruger til state/registeredUser
  registeredUser.value.push(newsletter.value)

  // Reset newsletter tekst felt når alert er løst
  newsletter.value = {
    email: null
  }
}
</script>

<template>
    <TheHeader/>
    <main>
        <h1>Klimaforandringernes konsekvenser for naturen</h1>
        <p>Klimaforandringerne påvirker alle områder af verden. Polarisen smelter, og vandstanden i havene stiger. I nogle områder bliver ekstreme vejrfænomener og nedbørsmængder mere almindelige, mens man i andre regioner oplever mere ekstreme hedebølger og tørker. Det er nødvendigt med en klimaindsats nu, ellers vil disse virkninger kun blive værre.</p>

        <!-- Vis throbber indtil den fjernes med script, derefter vis content -->
        <img v-if="throbber" class="throbber" src="https://upload.wikimedia.org/wikipedia/commons/7/7a/Ajax_loader_metal_512.gif" alt="throbber">
        <div v-else class="content">
            <div>
                <!-- Vis text fra state "titleOne" -->
                <h2 v-text="titleOne"></h2>
                <img class="images" src="../public/forest.jpg" alt="Tåget skov">
                <p>Klimaforandringerne sker så hurtigt, at mange plante- og dyrearter har svært ved at overleve. Der er klar dokumentation for, at biodiversiteten allerede reagerer på klimaforandringerne og fortsat vil gøre det. De direkte virkninger omfatter ændringer i fænologien (dyre- og plantearters adfærd og livscyklus), arternes tæthed og fordeling, sammensætningen af arternes samfund, levestedernes struktur og
                <!-- Vis "..." indtil toggleText er klikket, hvorefter den viser det resterende content -->
                <span v-if="!moreText.section1">...</span><span v-else> økosystemprocesser. Klimaforandringerne har desuden indirekte virkninger på biodiversiteten som følge af ændringer i anvendelsen af arealer og andre ressourcer. Disse kan være mere skadelige end de direkte virkninger på grund af deres omfang og hastighed. De indirekte virkninger omfatter: fragmentering og tab af levesteder, overudnyttelse, forurening af jord, vand og luft og spredningen af invasive arter. De vil yderligere reducere økosystemernes modstandsdygtighed over for klimaforandringer og deres evne til at opfylde væsentlige funktioner, f.eks. klimaregulering, fødevarer, ren luft og rent vand og forebyggelse af oversvømmelser eller erosion.</span></p>
                <!-- Toggle mellem Læs mere og læs mindre ved at trykke på knappen -->
                <button @click="toggleText('section1')">{{ moreText.section1 ? 'Læs mindre' : 'Læs mere' }}</button>
            </div>
            <div>
                <h2 v-text="titleTwo"></h2>
                <img class="images"src="../public/flood.jpg" alt="Oversvømmet kvarter">
                <p>Klimaforandringerne forventes at føre til større nedbør i mange områder. Øget nedbør over længere perioder vil hovedsageligt føre til flodoversvømmelser, mens korte, intense skybrud kan forårsage nedbørsoversvømmelser, hvor ekstreme regnskyl forårsager oversvømmelser, uden at et vandløb flyder over. Flodoversvømmelser er en almindelig naturkatastrofe i Europa, som sammen med storme har resulteret i dødsfald, ramt millioner af<span v-if="!moreText.section2">...</span><span v-else> mennesker og forårsaget enorme økonomiske tab i de seneste tre årtier. Klimaforandringerne vil sandsynligvis øge hyppigheden af oversvømmelser i hele Europa i de kommende år. Kraftige regnskyl forventes at blive mere almindelige og intense på grund af højere temperaturer, og det betyder, at pludselige oversvømmelser vil forekomme oftere i hele Europa. I nogle regioner kan visse risici, såsom oversvømmelser i begyndelsen af foråret, blive reduceret på kort sigt, når der er mindre snefald om vinteren, men den øgede risiko for pludselige oversvømmelser i bjergområder, der overbelaster flodsystemet, kan opveje den førnævnte reduktion af risiciene på mellemlangt sigt.</span></p>
                <button @click="toggleText('section2')">{{ moreText.section2 ? 'Læs mindre' : 'Læs mere' }}</button>
            </div>
            <div>
                <h2 v-text="titleThree"></h2>
                <img class="images"src="../public/fire.jpg" alt="Tørt område med skovbrand">
                <p>På grund af klimaforandringerne står mange europæiske regioner i forvejen over for hyppigere, mere alvorlige og langvarige tørkeperioder. En tørke er en usædvanlig og midlertidig mangel på vand, der skyldes en kombination af manglende nedbør og øget fordampning (på grund af høje temperaturer). Det adskiller sig fra vandknaphed, som er den strukturelle mangel på ferskvand året rundt som følge af overforbruget af<span v-if="!moreText.section3">...</span><span v-else>  vand. Tørke har ofte følgevirkninger, f.eks. på transportinfrastruktur, landbrug, skovbrug, vand og biodiversitet. Under tørke reduceres vandstanden i floder og grundvandsstanden, træernes og afgrødernes vækst hæmmes, forekomsten af angreb fra skadegørere øges, og der opstår flere naturbrande. I Europa medfører tørke årlige tab på ca. 9 mia. EUR, og det påvirker både landbruget, energisektoren og den offentlige vandforsyning. Ekstrem tørke bliver mere og mere almindelig i Europa, og de skader, tørken forårsager, bliver tilsvarende større. Med en gennemsnitlig global temperaturstigning på 3 °C forventes det, at tørke vil forekomme dobbelt så ofte, og at de absolutte årlige tab som følge af tørke i Europa vil stige til 40 mia. EUR om året, hvilket især vil få konsekvenser i Middelhavsområdet og Atlanterhavsregionerne. Hyppigere og mere alvorlig tørke vil gøre sæsonen for naturbrande længere og konsekvenserne af dem mere alvorlige, især i Middelhavsområdet. Klimaforandringerne udvider også det område, der er truet af naturbrande. Regioner, hvor naturbrande i øjeblikket ikke er et problem, kan blive risikoområder.</span></p>
                <button @click="toggleText('section3')">{{ moreText.section3 ? 'Læs mindre' : 'Læs mere' }}</button>
            </div>
            <div id="newsletter">
                <h3>Nyhedsbrev</h3>
                <p>Tilmeld dig nyhedsbrevet og vær den første til at høre mere omkring hvordan klimaforandringerne påvirker din hverdag</p>
                <form @submit.prevent="signUpNews" >
                <div>
                    <label for="email">Email: </label>
                    <input v-model="newsletter.email" type="email" id="email" name="email" placeholder="Email" required />
                </div>
                <button>Tilmeld</button> 
                </form>
            </div>
        </div>
    </main>
  
</template>

<style scoped>
/* ===============
   General content 
   =============== */
main{
    margin: auto;
    width: 45%;
}

h1, h2{
    font-family: Arial, Helvetica, sans-serif;
}

.images{
    width: 100%;
    height: 15rem;
    object-fit: cover;
}

/* ===============
   Throbber 
   =============== */

.throbber{
    display: block;
    margin-left: auto;
    margin-right: auto;
    width:  100px;
    padding: 10rem;
}


/* ===============
   Newsletter 
   =============== */

#newsletter{
    background: #bb8716;
    color: white;
    font-family: Arial, Helvetica, sans-serif;
    padding: 3rem 2rem;
    margin: 3rem 0;
}

#newsletter form{
    display: flex;
    padding: 1rem 0;
    gap: .5rem;
}

#newsletter div{
    padding: 0;
}

#newsletter button{
    background-color: black;
    border: none;
    color: white;
    padding: .1rem 1rem;
    text-decoration: none;
}


/* ===============
   Read more
   =============== */

.content button{
    border: none;
    background-color: white;
    text-decoration: underline;
    padding: 0;    
}

.content button:hover{
    border: none;
    background-color: white;
    color: red;
    text-decoration: underline;
    padding: 0;    
}

.content div{
    padding: 1.5rem 0;
}

</style>
