job("PD notify") {
    steps {
        shell('echo Hello World!')
    }
}


['tr-staging-v13', 'tr-staging-v14'].each { _env ->


    job("${_env}") {
        triggers {
            cron('* * * * * ')
        }
        publishers {
            downstream('PD notify', 'FAILURE')
        }

//        label ("health")
        steps {
            httpRequest{
                url('http://www.example.com')
                httpMode('GET')
                validResponseCodes("100:399")
//                validResponseContent("application/json")

            }

        }
    }
}
