from flask import Flask, render_template, request

app = Flask(__name__)

# Données fictives pour simuler un compte bancaire
user_data = {
    'nom': 'Thomas Rousseau',
    'solde': 50000,
    'compte_bloque': True,
    'frais_deblocage': 10000
}

@app.route('/')
def index():
    return render_template('login.html')

@app.route('/dashboard', methods=['POST'])
def dashboard():
    username = request.form['username']
    password = request.form['password']
    
    if username == 'thomas' and password == 'password123':  # Vérification fictive
        return render_template('dashboard.html', user=user_data)
    else:
        return "Identifiants incorrects"

if __name__ == "__main__":
    app.run(debug=True)
