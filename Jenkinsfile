def info = ""
pipeline{
  agent any

  environment{
    n1 = 10
    n2 = 5
    n_fichero = "resultado.txt"
  }

  options{
    timeout(time:5, unit: "MINUTES")
  }

  stages{
    stage("Operaciones Aritméticas"){
      steps{
        script{
          def suma = env.n1.toInteger() + env.n2.toInteger()
          def resta = env.n1.toInteger() - env.n2.toInteger()
          def multi = env.n1.toInteger() * env.n2.toInteger()
          def div = env.n1.toInteger() / env.n2.toInteger()
          info = "Los resultados de las operaciones de los números ${env.n1} y ${env.n2} son: \n Suma: ${suma} \n Resta: ${resta} \n Multiplicación: ${multi} \n División: ${div}"
          println "${info}"
        }
      }
    }
      stage("Ejecutar comando de CMD"){
        steps{
          bat "ipconfig /flushdns" 
        }
      }
      stage("Crear fichero"){
        steps{
          script{
            writefile(file: env.n_fichero, text: info)
            println "El fichero ${env.n_fichero} ha sido creado"
          }
        }
      }
    }
  
    post{
        always{
            echo "El pipeline ha sido ejecutado"
        }
        failure{
            echo 'El pipeline tiene errores'
        }
        success{
            echo "El pipeline se ejecutó de forma correcta"
        }
    }
  }
