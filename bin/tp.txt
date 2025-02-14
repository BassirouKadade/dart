import "dart:io";
import "dart:math";

int puissance3(int n, int degreP) {
  int r = 1;
  for (int i = 0; i < degreP; i++) {
    r *= n;
  }
  return r;
}

bool ArmStrong(int n) {
  int l = n;
  int somme = 0;
  int longueur = n.toString().length;

  while (l > 0) {
    int chiffre = l % 10;
    somme += puissance3(chiffre, longueur);
    l ~/= 10;
  }

  return somme == n;
}

bool IsNombrePremier(int n) {
  if (n < 2) return false;
  if (n == 2) return true;
  if (n % 2 == 0) return false;

  for (int i = 3; i <= sqrt(n); i += 2) {
    if (n % i == 0) {
      return false;
    }
  }
  return true;
}

void main() {
  stdout.write("Entrez un nombre : ");
  String? input = stdin.readLineSync();

  if (input != null) {
    int n = int.parse(input);
    if (ArmStrong(n)) {
      print("$n est un nombre d'Armstrong");
    } else {
      print("$n n'est pas un nombre d'Armstrong");
    }
  }
}
