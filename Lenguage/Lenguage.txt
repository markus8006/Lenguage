def interprete(code, vars, debug=False):
  code = code.replace("\n", " ")
  code = code.split(" ")
  code.remove("")
  for i in range(len(code)):
    if code[i] == "=":
      if code[i+1].startswith("'") and code[i+1].endswith("'"):
        code[i-1] = Texto(code[i-1], code[i+1], vars)
      elif code[i+1].isdigit():
        code[i-1] = Numero(code[i-1], int(code[i+1]), vars)
      else:
        code[i-1] = Decimal(code[i-1], code[i+1], vars)
    if code[i].startswith("Diga"):
      prompt = code[i].replace("Diga", "")
      prompt = prompt[:1] + ""
      prompt = prompt[:-1] + ""
      print(prompt)
  if debug:
    print(vars)



class Texto:
  def __init__(self, chave, valor, vars):
    self.valor = valor
    vars[chave] = {"Valor" : valor, "Tipo" : "Texto"}

class Numero:
  def __init__(self, chave, valor, vars):
    self.valor = valor
    vars[chave] = {"Valor" : valor, "Tipo" : "Numero"}

class Decimal:
  def __init__(self, chave, valor, vars):
    self.valor = valor
    vars[chave] = {"Valor" : valor, "Tipo" : "Decimal"}




class Main:
  def __init__(self, code, debug=False):
    self.vars = {}
    self.debug = debug
    self.code = code
  def run(self):
    if self.debug:
      interprete(self.code, self.vars, debug=True)
    else:
      interprete(self.code, self.vars)



dex = Main(Code, debug=True)
dex.run()

