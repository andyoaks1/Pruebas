import streamlit as st

st.set_page_config(page_title="Selector de Prueba Estadística", layout="centered")

st.title("🧪 Selector de Prueba Estadística")
st.write("Responde las preguntas y te recomendaré la prueba adecuada según tu situación.")

# ------------------------------
# Preguntas principales
# ------------------------------

st.header("1. Tipo de variable dependiente")
tipo_variable = st.selectbox(
    "¿Qué tipo de variable quieres analizar?",
    ["Selecciona una opción",
     "Numérica continua",
     "Ordinal",
     "Categórica (frecuencias)"]
)

if tipo_variable == "Selecciona una opción":
    st.stop()

# ------------------------------
# Si la variable es categórica → Chi-cuadrada
# ------------------------------
if tipo_variable == "Categórica (frecuencias)":
    st.subheader("Resultado recomendado:")
    st.success("👉 **Chi-cuadrada** (χ²)")
    st.write("Ideal para analizar asociación entre variables categóricas o diferencias entre frecuencias.")
    st.stop()

# ------------------------------
# Si la variable es numérica u ordinal → seguimos
# ------------------------------

st.header("2. Número de grupos o mediciones")
num_grupos = st.selectbox(
    "¿Cuántos grupos o mediciones quieres comparar?",
    ["Selecciona una opción", 2, 3, "Más de 3"]
)

if num_grupos == "Selecciona una opción":
    st.stop()

# ------------------------------
# Si son 2 grupos o mediciones
# ------------------------------
if num_grupos == 2:

    st.header("3. Relación entre los grupos")
    tipo_relacion = st.radio(
        "¿Los dos grupos son independientes o son las mismas personas medidas dos veces?",
        ["Independientes", "Relacionados (pareados)"]
    )

    # Normalidad
    st.header("4. Normalidad de los datos")
    normalidad = st.radio(
        "¿Tus datos muestran distribución normal?",
        ["Sí", "No", "No sé"]
    )

    # Decisión final
    if tipo_relacion == "Independientes":
        if normalidad == "Sí":
            prueba = "t de Student para muestras independientes"
        else:
            prueba = "U de Mann–Whitney"

    elif tipo_relacion == "Relacionados (pareados)":
        if normalidad == "Sí":
            prueba = "t de Student para muestras relacionadas (pareada)"
        else:
            prueba = "Wilcoxon"

    st.subheader("Resultado recomendado:")
    st.success(f"👉 **{prueba}**")

    st.stop()

# ------------------------------
# Si son 3 o más grupos
# ------------------------------

if num_grupos in [3, "Más de 3"]:

    st.header("3. Normalidad de los grupos")
    normalidad = st.radio(
        "¿Tus grupos cumplen normalidad?",
        ["Sí", "No", "Algunos sí y otros no", "No sé"]
    )

    # Decisión final
    if normalidad == "Sí":
        prueba = "ANOVA de un factor"
    else:
        prueba = "Kruskal–Wallis"

    st.subheader("Resultado recomendado:")
    st.success(f"👉 **{prueba}**")

    st.stop()

# ------------------------------
# Si la opción es correlación
# ------------------------------

# Solo aparece si variable es numérica u ordinal
st.header("¿Quieres analizar relación entre dos variables en lugar de comparar grupos?")
corr = st.radio(
    "¿Tu objetivo es ver cómo se relacionan dos variables?",
    ["No", "Sí"]
)

if corr == "Sí":
    tipo_variable2 = st.radio(
        "¿Tus datos son normales y la relación parece lineal?",
        ["Sí", "No", "No sé"]
    )

    if tipo_variable2 == "Sí":
        prueba = "Correlación de Pearson"
    else:
        prueba = "Correlación de Spearman"

    st.subheader("Resultado recomendado:")
    st.success(f"👉 **{prueba}**")

    st.stop()

# ------------------------------
# Si el objetivo es predicción → Regresión
# ------------------------------

st.header("¿Tu objetivo es predecir una variable?")
pred = st.radio(
    "¿Quieres predecir una variable dependiente a partir de otra?",
    ["No", "Sí"]
)

if pred == "Sí":
    st.subheader("Resultado recomendado:")
    st.success("👉 **Regresión lineal simple**")
