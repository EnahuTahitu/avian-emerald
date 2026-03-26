# \## The Prompt

# 

# I am replacing the Taillow and Swellow species entries with real European bird species. 

# 

# \*\*CRITICAL CONSTRAINT: CHARACTER LIMITS\*\*

# \- `.speciesName` must NOT exceed \*\*10 characters\*\*. If a name is longer, abbreviate it (e.g., "H. Sparrow").

# \- `.categoryName` must NOT exceed \*\*11 characters\*\*.

# 

# Apply the following changes:

# 

# \---

# 

# SPECIES\_TAILLOW → House Sparrow (Passer domesticus)

# 

# In gen\_3\_families.h, change ONLY these fields in the SPECIES\_TAILLOW block:

# &#x20; .speciesName = \_("H. Sparrow"),  // Abbreviated to fit 10-char limit

# &#x20; .categoryName = \_("Passerine"),

# &#x20; .baseHP        = 45,

# &#x20; .baseAttack    = 40,

# &#x20; .baseDefense   = 30,

# &#x20; .baseSpeed     = 85,

# &#x20; .baseSpAttack  = 30,

# &#x20; .baseSpDefense = 35,

# &#x20; .bodyColor = BODY\_COLOR\_BROWN,

# &#x20; .height = 2,

# &#x20; .weight = 3,

# &#x20; .description = COMPOUND\_STRING(

# &#x20;     "A quarrelsome bird common near human\\n"

# &#x20;     "settlements across Europe. It rolls\\n"

# &#x20;     "in dry dust or sand to rid its\\n"

# &#x20;     "feathers of parasites."),

# 

# \---

# 

# SPECIES\_SWELLOW → Barn Swallow (Hirundo rustica)

# 

# In gen\_3\_families.h, change ONLY these fields in the SPECIES\_SWELLOW block:

# &#x20; .speciesName = \_("B. Swallow"),  // Abbreviated to fit 10-char limit

# &#x20; .categoryName = \_("Swallow"),

# &#x20; .baseHP        = 60,

# &#x20; .baseAttack    = 70,

# &#x20; .baseDefense   = 45,

# &#x20; .baseSpeed     = 120,

# &#x20; .baseSpAttack  = 50,

# &#x20; .baseSpDefense = 45,

# &#x20; .bodyColor = BODY\_COLOR\_BLUE,

# &#x20; .height = 2,

# &#x20; .weight = 2,

# &#x20; .description = COMPOUND\_STRING(

# &#x20;     "A streamlined bird that migrates\\n"

# &#x20;     "thousands of kilometres each year.\\n"

# &#x20;     "It catches every insect it eats\\n"

# &#x20;     "without ever landing."),

