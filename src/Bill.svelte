<script lang="ts">
  let weLoveCookies: HTMLParagraphElement,
    title: HTMLInputElement,
    reasoning: HTMLInputElement,
    date: HTMLInputElement;

  function myFunction() {
    if (reasoning != null) {
      weLoveCookies.innerHTML =
        "Write me a proposed bill for the New Jersey legislature titled " +
        title.value +
        " along with 3 clauses: one clause that explains why it is important and " +
        reasoning.value +
        ", one clause with the actions it will take to achieve it, and one enactment clause under the previous clause that clearly explains the actions that will be made and states the date that it will be passed: " +
        date;
    } else {
      weLoveCookies.innerHTML =
        "Write me a proposed bill for the New Jersey legislature titled " +
        title.value +
        " along with 3 clauses: one clause that explains why it is important, one clause with the actions it will take to achieve it, and one enactment clause under the previous clause that clearly explains the actions that will be made and states the date that it will be passed";
    }
  }
</script>

<svelte:head>
  <title>OurState - Bill Archive</title>
</svelte:head>

<div class="format">
  <br />
  <br />
  <span>Please enter your bill's name:</span>
  <br />
  <input type="text" bind:this={title} placeholder="Title" />
  <br />
  <br />
  <span>Why do you want to pass this bill:</span>
  <br />
  <input type="text" bind:this={reasoning} placeholder="Reasoning" />
  <br />
  <br />
  <span> Subject: </span>
  <br />
  <select name="Subject" id="subject">
<option value="" selected="selected"></option>
<option value="ABORTION">ABORTION</option>
<option value="AGRICULTURE">AGRICULTURE</option><option value="FARMLAND">AGRICULTURE - FARMLAND PRESERVATION</option><option value="ALCOHOLIC BE">ALCOHOLIC BEVERAGES</option><option value="ANIMALS">ANIMALS</option><option value="ANIMAL LIC">ANIMALS - CONTROL AND LICENSING</option><option value="ANIMAL CRUEL">ANIMALS - CRUELTY AND WELFARE</option><option value="ARTS AND CUL">ARTS AND CULTURE</option><option value="AUTH - INTER">AUTHORITIES - INTERSTATE</option><option value="AUTH - LOCAL">AUTHORITIES - LOCAL</option><option value="AUTH - STATE">AUTHORITIES - STATE AND REGIONAL</option><option value="AVIATION">AVIATION</option><option value="BANKING">BANKING AND FINANCE</option><option value="CONSUMER FIN">BANKING AND FINANCE - CONSUMER FINANCE</option><option value="BOATS">BOATS AND BOAT SAFETY</option><option value="BONDS">BONDS</option><option value="CHARITIES">CHARITIES AND NON PROFIT ORGANIZATIONS</option><option value="CHILD SUPPOR">CHILD SUPPORT</option><option value="CHILDREN">CHILDREN</option><option value="ADOPTION">CHILDREN - ADOPTION</option><option value="CHILD ABUSE">CHILDREN - CHILD ABUSE</option><option value="CIVIL ACTION">CIVIL ACTIONS</option><option value="CHARITABLE">CIVIL ACTIONS - CHARITABLE IMMUNITY</option><option value="PERSONAL INJ">CIVIL ACTIONS - PERSONAL INJURY</option><option value="CIVIL RIGHTS">CIVIL RIGHTS</option><option value="CIVIL SVC">CIVIL SERVICE</option><option value="COMMEMORATIO">COMMEMORATIONS</option><option value="COMMERCE">COMMERCE</option><option value="COMMISSIONS">COMMISSIONS</option><option value="COMMUNICATIO">COMMUNICATIONS</option><option value="CONSUMER RIG">COMMUNICATIONS - CONSUMER RIGHTS AND PRIVACY</option><option value="INTERNET">COMMUNICATIONS - INTERNET</option><option value="TELEPHONE">COMMUNICATIONS - TELEPHONE</option><option value="TELEVISION">COMMUNICATIONS - TELEVISION</option><option value="COMMUNITY DE">COMMUNITY DEVELOPMENT</option><option value="CONSTITUTION">CONSTITUTIONAL AMENDMENTS</option><option value="CONSUMER AFF">CONSUMER AFFAIRS</option><option value="CONSUMER PRO">CONSUMER AFFAIRS - CONSUMER PROTECTION</option><option value="PRODUCT SAFE">CONSUMER AFFAIRS - PRODUCT SAFETY</option><option value="CORPORATIONS">CORPORATIONS</option><option value="CORRECTIONS">CORRECTIONS</option><option value="CRIME VICTIM">CRIME VICTIMS</option><option value="CRIMES">CRIMES AND PENALTIES</option><option value="CRIM PROCED">CRIMINAL PROCEDURES</option><option value="DOMESTIC REL">DOMESTIC RELATIONS</option><option value="CHILD CUSTOD">DOMESTIC RELATIONS - CHILD CUSTODY AND VISITATION</option><option value="DIVORCE">DOMESTIC RELATIONS - DIVORCE,  ALIMONY AND SPOUSAL SUPPORT</option><option value="MARRIAGE">DOMESTIC RELATIONS - MARRIAGE AND CIVIL UNIONS</option><option value="DOMESTIC VIO">DOMESTIC VIOLENCE</option><option value="ECONOMIC DEV">ECONOMIC DEVELOPMENT - INTERNATIONAL, STATE AND REGIONAL</option><option value="EDUCATION">EDUCATION</option><option value="CURRICULA">EDUCATION - CURRICULA</option><option value="EDUC FINANCE">EDUCATION - FINANCE</option><option value="ED HEALTH">EDUCATION - HEALTH</option><option value="SCH BOARDS">EDUCATION - SCHOOL BOARDS AND DISTRICTS</option><option value="SCH FACILITI">EDUCATION - SCHOOL FACILITIES</option><option value="SCH TRANS">EDUCATION - SCHOOL TRANSPORTATION</option><option value="TEACHERS">EDUCATION - TEACHERS AND SCHOOL EMPLOYEES</option><option value="ELECTIONS">ELECTIONS</option><option value="CAMP FINANCE">ELECTIONS - CAMPAIGN FINANCE</option><option value="ENERGY">ENERGY</option><option value="CONSERVATION">ENERGY - CONSERVATION</option><option value="ENVIRONMENT">ENVIRONMENT</option><option value="POLLUTION">ENVIRONMENT - AIR, NOISE AND WATER POLLUTION</option><option value="BEACHES">ENVIRONMENT - BEACHES AND SHORES</option><option value="FISH">ENVIRONMENT - FISH AND WILDLIFE</option><option value="FLOOD">ENVIRONMENT - FLOODING, DAMS AND LAKES</option><option value="HAZ SUBSTANC">ENVIRONMENT - HAZARDOUS AND TOXIC SUBSTANCES</option><option value="HIGHLANDS">ENVIRONMENT - HIGHLANDS AND PINELANDS</option><option value="OPEN SPACE">ENVIRONMENT - PARKS, FORESTS AND OPEN SPACE</option><option value="SITE REMED">ENVIRONMENT - SITE REMEDIATION AND BROWNFIELDS</option><option value="SOLID WASTE">ENVIRONMENT - SOLID WASTE AND RECYCLING</option><option value="WASTEWATER">ENVIRONMENT - WASTEWATER AND STORMWATER</option><option value="WATER SUPPLY">ENVIRONMENT - WATER SUPPLY</option><option value="ETHICS">ETHICS</option><option value="LOCAL ETHICS">ETHICS - LOCAL ETHICS</option><option value="FEDERAL REL">FEDERAL RELATIONS</option><option value="MEMORIALIZAT">FEDERAL RELATIONS - MEMORIALIZATIONS</option><option value="FOOD">FOOD</option><option value="GAMBLING">GAMBLING</option><option value="CASINOS">GAMBLING - CASINOS</option><option value="HORSE RACING">GAMBLING - HORSE RACING</option><option value="LOTTERIES">GAMBLING - LOTTERIES</option><option value="GOVERNOR">GOVERNOR</option><option value="HEALTH">HEALTH</option><option value="DISEASE">HEALTH - DISEASE</option><option value="EMER SVCS">HEALTH - EMERGENCY MEDICAL SERVICES</option><option value="HEALTH FAC">HEALTH - FACILITIES</option><option value="HEALTH FINAN">HEALTH - FINANCE</option><option value="PHARMACEUTIC">HEALTH - PHARMACEUTICALS</option><option value="HEALTH PROF">HEALTH - PROFESSIONALS</option><option value="HIGHER ED">HIGHER EDUCATION</option><option value="HISTORIC PRE">HISTORIC PRESERVATION</option><option value="HOUSING">HOUSING</option><option value="AFFORD HOUS">HOUSING - AFFORDABLE HOUSING</option><option value="CONDOS">HOUSING - CONDOMINIUMS, COOPERATIVES AND MOBILE HOMES</option><option value="CONSTR CODES">HOUSING - CONSTRUCTION CODES</option><option value="HOUSING FIN">HOUSING - FINANCE</option><option value="HOTELS">HOUSING - HOTELS AND MULTIPLE DWELLINGS</option><option value="LANDLORD">HOUSING - LANDLORD AND TENANT</option><option value="HUMAN SVCS">HUMAN SERVICES</option><option value="DEVEL DISAB">HUMAN SERVICES - DEVELOPMENTAL DISABILITIES</option><option value="DISABLED">HUMAN SERVICES - DISABLED</option><option value="DRUG ABUSE">HUMAN SERVICES - DRUG AND ALCOHOL ABUSE</option><option value="MEDICAID">HUMAN SERVICES - MEDICAID AND MEDICARE</option><option value="MENTAL HEALT">HUMAN SERVICES - MENTAL HEALTH</option><option value="PUB ASSIST">HUMAN SERVICES - PUBLIC ASSISTANCE</option><option value="IMMIGRATION">IMMIGRATION</option><option value="I &amp; R">INITIATIVE AND REFERENDUM</option><option value="INSURANCE">INSURANCE</option><option value="AUTO INSUR">INSURANCE - AUTOMOBILE INSURANCE</option><option value="HEALTH INSUR">INSURANCE - HEALTH INSURANCE</option><option value="INTERNAT AFF">INTERNATIONAL AFFAIRS</option><option value="INTERSTATE">INTERSTATE RELATIONS</option><option value="INTRASTATE">INTRASTATE RELATIONS</option><option value="JUDICIARY">JUDICIARY</option><option value="COURT ADMIN">JUDICIARY - COURT ADMINISTRATION</option><option value="JUDGES">JUDICIARY - JUDGES</option><option value="JUVENILE JUS">JUVENILE JUSTICE</option><option value="LABOR">LABOR</option><option value="TEMP DISAB">LABOR - TEMPORARY DISABILITY</option><option value="UNEMPL COMP">LABOR - UNEMPLOYMENT COMPENSATION</option><option value="WAGES">LABOR - WAGES AND BENEFITS</option><option value="WORKERS COMP">LABOR - WORKERS COMPENSATION</option><option value="LAND USE">LAND USE, PLANNING AND ZONING</option><option value="LEGISLATURE">LEGISLATURE</option><option value="LIBRARIES">LIBRARIES</option><option value="LOBBYING">LOBBYING</option><option value="LOCAL BUDGET">LOCAL BUDGET AND FINANCE</option><option value="LOC GOVT">LOCAL GOVERNMENT</option><option value="COUNTIES">LOCAL GOVERNMENT - COUNTIES</option><option value="MUNICIPALITI">LOCAL GOVERNMENT - MUNICIPALITIES</option><option value="STATE AID">LOCAL GOVERNMENT - STATE AID</option><option value="LOCAL OFFICE">LOCAL OFFICERS AND EMPLOYEES</option><option value="MARIJUANA">MARIJUANA</option><option value="MINORITY">MINORITY AND ETHNIC AFFAIRS</option><option value="MOTOR VEHICL">MOTOR VEHICLES</option><option value="COM VEHICLES">MOTOR VEHICLES - COMMERCIAL</option><option value="DUI">MOTOR VEHICLES - DUI</option><option value="MV OFFENSES">MOTOR VEHICLES - OFFENSES</option><option value="MV REGULATIO">MOTOR VEHICLES - REGULATION</option><option value="TRAFFIC SAFE">MOTOR VEHICLES - TRAFFIC SAFETY</option><option value="DISASTERS">NATURAL DISASTERS</option><option value="NJ HISTORY">NEW JERSEY - HISTORY AND SYMBOLS</option><option value="PAROLE">PAROLE</option><option value="PENSIONS">PENSIONS</option><option value="PENSIONS POL">PENSIONS - POLICE AND FIREFIGHTERS</option><option value="PENSIONS PUB">PENSIONS - PUBLIC EMPLOYEES</option><option value="PENSIONS TEA">PENSIONS - TEACHERS</option><option value="PROBATION">PROBATION</option><option value="PROPERTY">PROPERTY</option><option value="EMINENT">PROPERTY - EMINENT DOMAIN</option><option value="LOCAL PROP">PROPERTY - LOCAL</option><option value="PROSECUTORS">PROSECUTORS</option><option value="DISCLOSURE">PUBLIC CONTRACTS - DISCLOSURES</option><option value="LOCAL CONT">PUBLIC CONTRACTS - LOCAL</option><option value="ST CONTRACTS">PUBLIC CONTRACTS - STATE</option><option value="PUB EMPLOYEE">PUBLIC EMPLOYEES</option><option value="PUB EMP BENE">PUBLIC EMPLOYEES - BENEFITS</option><option value="PUBLIC FEES">PUBLIC FEES</option><option value="PUB RECORDS">PUBLIC RECORDS, NOTICE AND MEETINGS</option><option value="PUB SAFETY">PUBLIC SAFETY</option><option value="EMERG MGMT">PUBLIC SAFETY - EMERGENCY MANAGEMENT</option><option value="FIREFIGHTERS">PUBLIC SAFETY - FIREFIGHTERS</option><option value="HOMELAND SEC">PUBLIC SAFETY - HOMELAND SECURITY</option><option value="POLICE">PUBLIC SAFETY - POLICE</option><option value="SEX OFFEND">PUBLIC SAFETY - SEX OFFENDERS</option><option value="WEAPONS">PUBLIC SAFETY - WEAPONS</option><option value="PUBLIC UTIL">PUBLIC UTILITIES</option><option value="PROFESSIONS">REGULATED PROFESSIONS</option><option value="REGULATORY">REGULATORY OVERSIGHT</option><option value="SCI AND TECH">SCIENCE AND TECHNOLOGY</option><option value="SR CITIZENS">SENIOR CITIZENS</option><option value="SMOKING">SMOKING AND TOBACCO</option><option value="SPECIAL LEG">SPECIAL LEGISLATION</option><option value="SPORTS">SPORTS AND RECREATION</option><option value="STATE BUDGT">STATE BUDGET AND FINANCE</option><option value="SUPPL APPROP">STATE BUDGET AND FINANCE - SUPPLEMENTAL APPROPRIATIONS</option><option value="STATE GOVT">STATE GOVERNMENT</option><option value="STATE DEPTS">STATE GOVERNMENT - DEPARTMENTS AND AGENCIES</option><option value="STATE OFFICE">STATE GOVERNMENT - OFFICERS AND EMPLOYEES</option><option value="TAXATION">TAXATION</option><option value="ALCO TAXES">TAXATION - ALCOHOL, GASOLINE AND TOBACCO TAXES</option><option value="BUS TAXES">TAXATION - BUSINESS TAXES</option><option value="INCOME TAX">TAXATION - PERSONAL INCOME TAX</option><option value="PROPERTY TAX">TAXATION - PROPERTY TAX</option><option value="PUB UTIL TAX">TAXATION - PUBLIC UTILITIES TAX</option><option value="SALES TAX">TAXATION - SALES TAX</option><option value="TERRORISM">TERRORISM</option><option value="TRANSPORT">TRANSPORTATION</option><option value="FREIGHT RAIL">TRANSPORTATION - FREIGHT RAIL</option><option value="HIGHWAYS">TRANSPORTATION - HIGHWAYS, ROADS AND BRIDGES</option><option value="TRANS PLAN">TRANSPORTATION - PLANNING, FINANCE AND ECONOMIC DEVELOPMENT</option><option value="PUBLIC TRANS">TRANSPORTATION - PUBLIC TRANSIT</option><option value="VETERANS">VETERANS AND MILITARY</option><option value="WILLS">WILLS, TRUSTS AND ESTATES</option><option value="WOMEN">WOMEN</option>  
</select>
<br />
<br />
<span
    > (Optional) What is the date you want to pass this bill by? In [Month],[Day],[Year]
    format:</span
  >
  <br />
  <input type="text" bind:this={date} placeholder="Date" />
  <br />
  <br />
  <button on:click={myFunction}>Submit</button>
</div>

<p bind:this={weLoveCookies} />

  <!-- powr BEGIN --><div class="powr-form-builder" id="sharethis-form-builder-651a0aefd43c16001201d81d"></div><!-- powr END -->

<style>
  .format {
    margin-left: 5rem;
    white-space: flex;
  }

  span {
    font-size: 2rem;
  }

  input {
    border: 2px var(--fg) solid;
    width: 20rem;
    height: 2rem;
    font-size: 1.5rem;
    background-color: var(--bg);
  }

  button {
    padding: .625rem;
    font-size: 1.25rem;
    border: none;
    background-color: var(--blue);
    color: var(--bg);
    cursor: pointer;
    border-radius: 1rem;
  }

  button:hover {
    background-color: var(--dim-bg);
    color: var(--fg);
    border-radius: .5rem;
  }

  select {
    border: 2px var(--fg) solid;
    width: 20rem;
    height: 2rem;
    font-size: 1.5rem;
    background-color: var(--bg);
  }
</style>
