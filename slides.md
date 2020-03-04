---
title: What Kubernetes and Voldemort have in common
pdf: kubernetes-horcrux-slides.pdf
standalone: kubernetes-horcrux-slides.html
transition: slide
backgroundTransition: fade
slideNumber: true
controls: false
controlsTutorial: false
asciinema: false
---

<link href="assets/css/font-awesome.min.css" rel="stylesheet">

# {bgcss=tw-colorful .light-on-dark}

<div class="xkcd"><span class="xkcd">WHAT</span><br/><span class="xkcd"><font size="72">KUBERNETES</font></span><br/><span class="xkcd">AND</span><br/><span class="xkcd"><font size="72">VOLDEMORT</font></span><br/><span class="xkcd">HAVE IN COMMON</span></div>

# THE VILLAIN'S DILEMMA {bgcss=tw-bg-yellow}

```render_a2sketch


           x Count Dooku 

                                      x Marisa Coulter

                          #-------------#
 x Supreme Leader Snoke   |[c]          |        x Pennywise
                          | x Voldemort |                       x Cthulhu
                          |             |                  
                          #-------------#                  
                                           x Tom Ripley

<------------------------------------------------------------------------>
 pathetic                                                      terrifying



[c]: {"a2s:type": "circle", "a2s:delref": true, "fill": "transparent", "fillStyle": "solid"}
```

# THE HORCRUX STRATEGY {bgcss=tw-bg-light-blue}

<img src="assets/img/snake.svg" width="500px"/>

<div class="tiny">Source: <a href="https://pixabay.com/en/snake-animal-nature-reptile-3254415/">Pixabay</a></div>

# ORCHESTRATION "WARS" {bgcss=tw-bg-purple .light-on-dark}

# DISTRIBUTED DEPLOYMENT {bgcss=tw-bg-extra-light-blue}

```render_a2sketch
                      #------------#
                      |[c]         |
                      | Users      |
                      |            |
                      #-----#------#
                            |
                            v
                      #-----#------#
                      |[w]         |
                      | Service    |
                      |            |
                      #-----#------#
                            |
             #--------------#--------------#
             |                             |
             v              |              v
#------------#------------.   #------------#------------#
|[p]         |[p]         | | |[o]         |[o]         |
| Container  | Container  |   | Container  | Container  |
|            |            | | |            |            |
#------------#------------#   #------------#------------#
|[w]                      | | |[w]                      |
| Host       #------------#   | Host       #------------#
| [zone=a]   |[g]kernel   | | | [zone=b]   |[g]kernel   |        
'------------#------------#   '------------#------------#
                            |
Availability zone a           Availability zone b
                            |

[c]: {"a2s:type": "cloud", "a2s:delref": true, "fill": "#fff", "fillStyle": "solid"}
[w]: {"a2s:delref": true, "fill": "#fff", "fillStyle": "solid", "strokeStyle": "#000"}
[g]: {"a2s:delref": true, "fill": "transparent", "fillStyle": "solid", "strokeStyle": "#000"}
[p]: {"a2s:delref": true, "fill": "#ef5ba1", "fillStyle": "solid", "strokeStyle": "#000"}
[o]: {"a2s:delref": true, "fill": "#f99c41", "fillStyle": "solid"}
```

# CANARY DEPLOYMENT {bgcss=tw-bg-yellow}

```render_a2sketch

                      #------------#
                      |[c]         |
                      | Users      |
                      |            |
                      #-----#------#
               95%          |           5%
             #--------------#--------------#
             |                             |
             v                             v
       #-----#------#                #-----#------#
       |[p]         |                |[b]         |
       | v1.0.0     |                | v1.0.1-beta|
       |            |                |            |
       #------------#                #------------#


[c]: {"a2s:type": "cloud", "a2s:delref": true, "fill": "#fff", "fillStyle": "solid"}
[w]: {"a2s:delref": true, "fill": "#fff", "fillStyle": "solid", "strokeStyle": "#000"}
[g]: {"a2s:delref": true, "fill": "#ddd", "fillStyle": "solid", "strokeStyle": "#000"}
[p]: {"a2s:delref": true, "fill": "#ef5ba1", "fillStyle": "solid", "strokeStyle": "#000"}
[b]: {"a2s:delref": true, "fill": "#f99c41", "fillStyle": "solid", "strokeStyle": "#000"}
```

# ZERO TRUST DEPLOYMENT {bgcss=tw-bg-yellow}

```render_a2sketch

                      #------------#       #-----------#    
                      |[c]         |       |[s]        |     
                      | Users      | - - - | Dashboard |     
                      |            |       |           |      
                      #-----#------#       #-----------#      
                            |
             #--------------#--------------#
             |                             |
             v                             v
       #-----#------#                #-----#------#
       |[p]         |                |[b]         |
       | Service a  #<--------------># Service b  |
       |            |  mutual TLS    |            |
       #------------#                #------------#

                       Service mesh  


[c]: {"a2s:type": "cloud", "a2s:delref": true, "fill": "#fff", "fillStyle": "solid"}
[w]: {"a2s:delref": true, "fill": "#fff", "fillStyle": "solid", "strokeStyle": "#000"}
[g]: {"a2s:delref": true, "fill": "#ddd", "fillStyle": "solid", "strokeStyle": "#000"}
[s]: {"a2s:type": "computer", "a2s:delref": true, "fill": "#fff", "fillStyle": "solid"}
[p]: {"a2s:delref": true, "fill": "#ef5ba1", "fillStyle": "solid", "strokeStyle": "#000"}
[b]: {"a2s:delref": true, "fill": "#f99c41", "fillStyle": "solid", "strokeStyle": "#000"}
```

# THE COMPETITIVE ENVIRONMENT {bgcss=tw-bg-purple .light-on-dark}

# ALL HAPPY FAMILIES {bgcss=tw-bg-extra-light-blue}

```render_a2sketch
.--------------------------------------------------------------.
|[c]                                                           |
|                             Fleet                            |
|           Docker Swarm                                       |
|                                 OpenShift (1-2)              |
|                      Kubernetes                              |
|     Apache Mesos                                             |
|                             Elastic Container Service        |
|            Heroku                                            |
|                    Cloud Foundry                             |
|                                   Panamax                    |
|          Shipyard                                            |
|                                       Portainer              |
|                                                              |
'--------------------------------------------------------------'

[c]: {"a2s:type": "cloud", "a2s:delref": true, "fill": "#fff", "fillStyle": "solid"}
```

<aside class="notes" data-markdown>
This position (there are platforms for end users and others for platform builders) is absolutely fine in a vibrant ecosystem of container schedulers. There's no doubt developers love Docker Swarm, for example.
</aside>

# SPLENDID ISOLATION {bgcss=tw-bg-extra-light-blue} 

```render_a2sketch
.--------------------------------------------------------------.
|[c]                                                           |
|                                                              |
|                                                              |
|                                                              |
|                      Kubernetes                              |
|                                                              |
|                                                              |
|                                                              |
|                                                              |
|                                                              |
|                                                              |
|                                                              |
|                                                              |
'--------------------------------------------------------------'

[c]: {"a2s:type": "cloud", "a2s:delref": true, "fill": "#fff", "fillStyle": "solid"}
```

<aside class="notes" data-markdown>
However, that is not the ecosystem we have today. It seems odd to let Kubernetes displace all contenders only to say that it's for platform builders only.
</aside>

# THE HORCRUX STRATEGY {bgcss=tw-bg-purple .light-on-dark}

# VENDOR SHARDING {bgcss=tw-bg-extra-light-blue}

```render_a2sketch
#-------------------------#   #-------------------------#       
|[p]                      |   |[b]                      |      
|                         |   |        IBM              |      
|      Microsoft          |   |        Red Hat          |       
|                         |   |        CoreOS           |      
|                         |   |                         |      
#-------------------------#   #-------------------------#       

          #----------------------------------#
          |[c]                               |
          |                                  |
          |              Google              |
          |                                  |
          |                                  |
          #----------------------------------#

#-------------------------#   #-------------------------#       
|[d]                      |   |[e]                      |      
|                         |   |                         |       
|        VMware           |   |        Alibaba          |        
|                         |   |                         |       
|                         |   |                         |       
#-------------------------#   #-------------------------#       

         Cloud Native Computing Foundation (CNCF)
 
[c]: {"a2s:delref": true, "fill": "#fff", "fillStyle": "solid"}
[p]: {"a2s:delref": true, "fill": "#ef5ba1", "fillStyle": "solid", "strokeStyle": "#000"}
[b]: {"a2s:delref": true, "fill": "#f99c41", "fillStyle": "solid", "strokeStyle": "#000"}
[d]: {"a2s:delref": true, "fill": "#27bdce", "fillStyle": "solid", "strokeStyle": "#000"}
[e]: {"a2s:delref": true, "fill": "#00aa5b", "fillStyle": "solid", "strokeStyle": "#000"}

```

# PRECONDITIONS {bgcss=tw-bg-extra-light-blue}

```render_a2sketch

.---------------------------------------------------.
|[w]                                                |
| open source                                       |
|                                                   |
#---------------------------------------------------#
|[w]                                                |
| neutral IP ownership                              |
|                                                   |
#---------------------------------------------------#
|[w]                                                |
| extensibility                                     |
|                                                   |
'---------------------------------------------------'

[w]: {"a2s:delref": true, "fill": "#fff", "fillStyle": "solid"}
[p]: {"a2s:delref": true, "fill": "#ef5ba1", "fillStyle": "solid", "strokeStyle": "#000"}
[b]: {"a2s:delref": true, "fill": "#f99c41", "fillStyle": "solid", "strokeStyle": "#000"}
[d]: {"a2s:delref": true, "fill": "#27bdce", "fillStyle": "solid", "strokeStyle": "#000"}
[e]: {"a2s:delref": true, "fill": "#00aa5b", "fillStyle": "solid", "strokeStyle": "#000"}


```

# PRECONDITIONS {bgcss=tw-bg-extra-light-blue}

```render_a2sketch

.---------------------------------------------------.
|[p]                                                |
| open source - MIT                                 |
|                                                   |
#---------------------------------------------------#
|[w]                                                |
| neutral IP ownership                              |
|                                                   |
#---------------------------------------------------#
|[w]                                                |
| extensibility                                     |
|                                                   |
'---------------------------------------------------'

[w]: {"a2s:delref": true, "fill": "#fff", "fillStyle": "solid"}
[p]: {"a2s:delref": true, "fill": "#ef5ba1", "fillStyle": "solid", "strokeStyle": "#000"}
[b]: {"a2s:delref": true, "fill": "#f99c41", "fillStyle": "solid", "strokeStyle": "#000"}
[d]: {"a2s:delref": true, "fill": "#27bdce", "fillStyle": "solid", "strokeStyle": "#000"}
[e]: {"a2s:delref": true, "fill": "#00aa5b", "fillStyle": "solid", "strokeStyle": "#000"}

```
<small>A suitably permissive license is a necessary but not sufficient precondition.</small>

# PRECONDITIONS {bgcss=tw-bg-extra-light-blue}

```render_a2sketch

.---------------------------------------------------.
|[p]                                                |
| open source - MIT                                 |
|                                                   |
#---------------------------------------------------#
|[b]                                                |
| neutral IP ownership - CNCF                       |
|                                                   |
#---------------------------------------------------#
|[w]                                                |
| extensibility                                     |
|                                                   |
'---------------------------------------------------'

#---------------------------------------------------#
|[q]                                                |
|                                                   |
|                                                   |
| K8s would *not* be what it is today without       |
| neutral IP ownership... K8s has spawned an entire |
| ecosystem *because* it can be used by consuming   |
| projects/products without fear.                   |
|                                                   |
|                             - Matt Klein          |
|                                                   |
|                                                   |
|                                                   |
#---------------------------------------------------#
[q]: {"a2s:type": "quote-sw", "a2s:delref": true, "fill": "#f99c41", "fillStyle": "solid"}
[w]: {"a2s:delref": true, "fill": "#fff", "fillStyle": "solid"}
[p]: {"a2s:delref": true, "fill": "#ef5ba1", "fillStyle": "solid", "strokeStyle": "#000"}
[b]: {"a2s:delref": true, "fill": "#f99c41", "fillStyle": "solid", "strokeStyle": "#000"}
[d]: {"a2s:delref": true, "fill": "#27bdce", "fillStyle": "solid", "strokeStyle": "#000"}
[e]: {"a2s:delref": true, "fill": "#00aa5b", "fillStyle": "solid", "strokeStyle": "#000"}
```
<div class="tiny">Source: <a href="https://twitter.com/mattklein123/status/1229513052673855488?ref_src=twsrc%5Etfw">@mattklein123 on Twitter</a>, 17 February 2020.</div> 

# PRECONDITIONS {bgcss=tw-bg-extra-light-blue}

```render_a2sketch

.---------------------------------------------------.
|[p]                                                |
| open source - MIT                                 |
|                                                   |
#---------------------------------------------------#
|[b]                                                |
| neutral IP ownership - CNCF                       |
|                                                   |
#---------------------------------------------------#
|[d]                                                |
| extensibility - controllers and operators         |
|                                                   |
'---------------------------------------------------'

[w]: {"a2s:delref": true, "fill": "#fff", "fillStyle": "solid"}
[p]: {"a2s:delref": true, "fill": "#ef5ba1", "fillStyle": "solid", "strokeStyle": "#000"}
[b]: {"a2s:delref": true, "fill": "#f99c41", "fillStyle": "solid", "strokeStyle": "#000"}
[d]: {"a2s:delref": true, "fill": "#27bdce", "fillStyle": "solid", "strokeStyle": "#000"}
[e]: {"a2s:delref": true, "fill": "#00aa5b", "fillStyle": "solid", "strokeStyle": "#000"}

```

<small>**Controllers** add custom processing to the core reconciliation loop.</small>
<small>When paired with custom resource definitions, they are known as **operators**.</small>

# OPERATORS {bg=#fff44d}

```render_a2sketch
#--------------------------#     #-------------------------#       
|[p]                       |     |[b]                      |      
|                          |     |                         |      
|Custom Resource Definition+<-+->+        Controller       |       
|  (e.g. "VaultService")   |  |  | (backup, upgrade, etc.) |      
|                          |  |  |                         |      
#--------------------------#  |  #-------------------------#       
                              |
                              |
                              v
                 #------------+-------------#  
                 |[s]                       | 
                 |                          |
                 |                          |
                 |                          | 
                 |   Cluster state (etcd)   |
                 |   Persistent Volumes     |
                 |        ConfigMaps        |
                 |          Secrets         |
                 |                          |
                 #--------------------------#  


[p]: {"a2s:delref": true, "fill": "#ef5ba1", "fillStyle": "solid", "strokeStyle": "#000"}
[b]: {"a2s:delref": true, "fill": "#f99c41", "fillStyle": "solid", "strokeStyle": "#000"}
[s]: {"a2s:type":"storage", "a2s:delref": true, "fillStyle": "solid", "fill": "#ffffff"}
```

# STATEFUL WORKLOADS {bgcss=tw-bg-extra-light-blue}

```render_a2sketch
#------------------------------------------------------------------#
|[q]                                                               |
|                                                                  |
|                                                                  |
|                                                                  |
|    Stateless is Easy, Stateful is Hard.                          |
|                                                                  |
|                                   - Brandon Philips (2016)       |
|                                                                  |
|                                                                  |
|                                                                  |
#------------------------------------------------------------------#

[q]: {"a2s:type": "quote-sw", "a2s:delref": true, "fill": "#ef5ba1", "fillStyle": "solid"}
```

<div class="tiny">Source: <a href="https://coreos.com/blog/introducing-operators.html">coreos.com/blog/introducing-operators.html</a></div> 

# PIZZA EFFECTS {bgcss=tw-bg-extra-light-blue}

```{.render_plantuml args="-Sbackgroundcolor=transparent"}
@startuml
skinparam BoxPadding 10
Kubernetes->"Red Hat OpenShift" : beware stateful applications
"Red Hat OpenShift"->Kubernetes : application templates (2015)
Kubernetes->"CoreOS Tectonic" : stateful applications still hard
"CoreOS Tectonic"->Kubernetes : etcd operator with third-party resources (2016)
Kubernetes->"CoreOS Tectonic" : Custom Resource Definitions
"CoreOS Tectonic"->Kubernetes : Operator Framework and SDK (2018)
"CoreOS Tectonic"->"Red Hat OpenShift" : merges with (2019)
@enduml
```

<aside class="notes" data-markdown>
</aside>


# CORPORATE SPONSORS {bg=#fff44d}

Vault operator<br/>
<img src="assets/img/CoreOS.svg" width="200px"/>

MySQL operator<br/>
<img src="assets/img/Oracle_logo.svg" width="200px"/>

PostgreSQL operator<br/>
<img src="assets/img/Zalando_logo.svg" width="200px"/>

# MEANWHILE IN THE CLOUD {bgcss=tw-bg-purple .light-on-dark}

# FIRST MOVER ADVANTAGE {bg=#fff44d}

```render_vegalite
{
    "$schema": "https://vega.github.io/schema/vega-lite/v2.0.json",
    "data": {
        "values": [
            {"regions": 1, "date": "2006", "symbol": "AMZN" },
            {"regions": 1, "date": "2007", "symbol": "AMZN" },
            {"regions": 2, "date": "2008", "symbol": "AMZN" },
            {"regions": 3, "date": "2009", "symbol": "AMZN" },
            {"regions": 4, "date": "2010", "symbol": "AMZN" },
            {"regions": 8, "date": "2011", "symbol": "AMZN" },
            {"regions": 9, "date": "2012", "symbol": "AMZN" },
            {"regions": 10, "date": "2013", "symbol": "AMZN" },
            {"regions": 11, "date": "2014", "symbol": "AMZN" },
            {"regions": 11, "date": "2015", "symbol": "AMZN" },
            {"regions": 16, "date": "2016", "symbol": "AMZN" },
            {"regions": 16, "date": "2017", "symbol": "AMZN" },
            {"regions": 17, "date": "2018", "symbol": "AMZN" },
            {"regions": 0, "date": "2006", "symbol": "GOOG" },
            {"regions": 0, "date": "2007", "symbol": "GOOG" },
            {"regions": 0, "date": "2008", "symbol": "GOOG" },
            {"regions": 0, "date": "2009", "symbol": "GOOG" },
            {"regions": 0, "date": "2010", "symbol": "GOOG" },
            {"regions": 4, "date": "2011", "symbol": "GOOG" },
            {"regions": 6, "date": "2012", "symbol": "GOOG" },
            {"regions": 8, "date": "2013", "symbol": "GOOG" },
            {"regions": 10, "date": "2014", "symbol": "GOOG" },
            {"regions": 12, "date": "2015", "symbol": "GOOG" },
            {"regions": 14, "date": "2016", "symbol": "GOOG" },
            {"regions": 16, "date": "2017", "symbol": "GOOG" },
            {"regions": 18, "date": "2018", "symbol": "GOOG" },
            {"regions": 0, "date": "2006", "symbol": "MSFT" },
            {"regions": 0, "date": "2007", "symbol": "MSFT" },
            {"regions": 0, "date": "2008", "symbol": "MSFT" },
            {"regions": 0, "date": "2009", "symbol": "MSFT" },
            {"regions": 2, "date": "2010", "symbol": "MSFT" },
            {"regions": 8, "date": "2011", "symbol": "MSFT" },
            {"regions": 14, "date": "2012", "symbol": "MSFT" },
            {"regions": 20, "date": "2013", "symbol": "MSFT" },
            {"regions": 26, "date": "2014", "symbol": "MSFT" },
            {"regions": 32, "date": "2015", "symbol": "MSFT" },
            {"regions": 39, "date": "2016", "symbol": "MSFT" },
            {"regions": 46, "date": "2017", "symbol": "MSFT" },
            {"regions": 54, "date": "2018", "symbol": "MSFT" },
            {"regions": 0, "date": "2008", "symbol": "BABA" },
            {"regions": 3, "date": "2009", "symbol": "BABA" },
            {"regions": 3, "date": "2010", "symbol": "BABA" },
            {"regions": 3, "date": "2011", "symbol": "BABA" },
            {"regions": 3, "date": "2012", "symbol": "BABA" },
            {"regions": 3, "date": "2013", "symbol": "BABA" },
            {"regions": 4, "date": "2014", "symbol": "BABA" },
            {"regions": 5, "date": "2015", "symbol": "BABA" },
            {"regions": 9, "date": "2016", "symbol": "BABA" },
            {"regions": 12, "date": "2017", "symbol": "BABA" },
            {"regions": 20, "date": "2018", "symbol": "BABA" }
        ]
    },
    "width": 600,
    "height": 300,
    "mark": "bar",
    "encoding": {
        "x": {
            "timeUnit": "year", "field": "date", "type": "temporal"
        },
        "y": {
            "field": "regions", "type": "quantitative", "scale": {"domain": [0, 120]}
        },
        "color": { "field": "symbol", "type": "nominal", "scale": {
          "domain": [ "AMZN", "GOOG", "MSFT", "BABA" ],
          "range": [ "#fe17bf", "#3364c0", "#27bdce", "#00aa5b" ]
        } }
    },
    "config": {
        "axis": {
            "labelFont": "sans-serif",
            "labelFontSize": 18,
            "titleFont": "sans-serif",
            "titleFontSize": 18
        },
        "axisX": {
            "labelAngle": 0
        },
        "bar": {
            "continuousBandSize": 20
        }
    }
}
```

# A VERY PUBLIC BREAKUP {bgcss=tw-bg-extra-light-blue}

```render_a2sketch
#-------------------------#   #-------------------------#       
|[p]                      |   |[b]                      |      
|                         |   |                         |      
|    Secrets Manager      |   |           RDS           |       
|                         |   |                         |      
|                         |   |                         |      
#-------------------------#   #-------------------------#       

          #----------------------------------#
          |[c]                               |
          |                                  |
          |                EKS               |
          |                                  |
          |                                  |
          #----------------------------------#

#-------------------------#   #-------------------------#       
|[d]                      |   |[e]                      |      
|                         |   |                         |       
|      CodePipeline       |   |          SQS            |        
|                         |   |                         |       
|                         |   |                         |       
#-------------------------#   #-------------------------#       

                   Amazon Web Services

[c]: {"a2s:delref": true, "fill": "#fff", "fillStyle": "solid"}
[p]: {"a2s:delref": true, "fill": "#ef5ba1", "fillStyle": "solid", "strokeStyle": "#000"}
[b]: {"a2s:delref": true, "fill": "#f99c41", "fillStyle": "solid", "strokeStyle": "#000"}
[d]: {"a2s:delref": true, "fill": "#27bdce", "fillStyle": "solid", "strokeStyle": "#000"}
[e]: {"a2s:delref": true, "fill": "#00aa5b", "fillStyle": "solid", "strokeStyle": "#000"}

```

<small>AWS perfected the use of services based on open source products.</small>
<small>In 2016 MongoDB responded with the <a href="https://www.mongodb.com/community/licensing">Server Side Public License</a>.</small>

# TRADE WAR {bg=#fff44d}

<small>Alibaba Cloud became a CNCF Gold Member and upgraded to Platinum in 2017.</small>

<small>Alibaba affiliate Ant Financial, Baidu and Tencent also became Gold Members.</small>

<img src="assets/img/android.svg"/>

# HORCRUX LIFE {bgcss=tw-bg-extra-light-blue}

```render_a2sketch
  
     #-----------------------------------------------------------#
     |[w]                                                        |
     | #-------------------------#   #-------------------------# |      
     | |[p]                      |   |[b]                      | |    
     | |                         |   |                         | |    
     | |     Vault operator      |   |   PostgreSQL operator   | |     
     | |                         |   |                         | |    
     | |                         |   |                         | |    
     | #-------------------------#   #-------------------------# |     
     |                                                           |              
     |                                                           |    
     |                        Kubernetes                         |    
     |                                                           |     
     |                                                           |     
     | #-------------------------#   #-------------------------# |     
     | |[d]                      |   |[e]                      | |    
     | |                         |   |                         | |     
     | |   Jenkins X operator    |   |     Kafka operator      | |      
     | |       (Tekton)          |   |                         | |     
     | |                         |   |                         | |     
     | #-------------------------#   #-------------------------# |     
     |                                                           |     
     #-----------------------------------------------------------#     
           Any cloud offering a managed Kubernetes service 

[w]: {"a2s:delref": true, "fill": "#fff", "fillStyle": "solid"}
[p]: {"a2s:delref": true, "fill": "#ef5ba1", "fillStyle": "solid", "strokeStyle": "#000"}
[b]: {"a2s:delref": true, "fill": "#f99c41", "fillStyle": "solid", "strokeStyle": "#000"}
[d]: {"a2s:delref": true, "fill": "#27bdce", "fillStyle": "solid", "strokeStyle": "#000"}
[e]: {"a2s:delref": true, "fill": "#00aa5b", "fillStyle": "solid", "strokeStyle": "#000"}
```

# ASPIRING CLOUD VENDORS {bgcss=tw-bg-extra-light-blue}

```render_a2sketch

IS THE HORCRUX LIFE FOR ME?                                
                                                YES!     NOPE                 
                                            #---------#---------#          
                                            |[g]      |[w]      |          
Did AWS steal a multi-year march on you?    |    ✓    |    ✗    |          
                                            |         |         |          
                                            #---------#---------#          
                                            |[g]      |[w]      |          
Are you at risk of US trade sanctions?      |    ✓    |    ?    |          
                                            |         |         |          
                                            #---------#---------#          
                                            |[g]      |[w]      |          
Are you a bazaar kind of company?           |    ✓    |    ?    |          
                                            |         |         |          
                                            #---------#---------#          
                                                                             

[g]: {"a2s:delref": true, "fill": "#00aa5b", "fillStyle": "solid"}
[w]: {"a2s:delref": true, "fill": "#fff", "fillStyle": "solid"}
[p]: {"a2s:delref": true, "fill": "#ef5ba1", "fillStyle": "solid", "strokeStyle": "#000"}
[b]: {"a2s:delref": true, "fill": "#f99c41", "fillStyle": "solid", "strokeStyle": "#000"}
[d]: {"a2s:delref": true, "fill": "#27bdce", "fillStyle": "solid", "strokeStyle": "#000"}
[e]: {"a2s:delref": true, "fill": "#00aa5b", "fillStyle": "solid", "strokeStyle": "#000"}

```

# THANK YOU {bgcss=tw-colorful .light-on-dark}

<small>Slides built with <a href="https://github.com/arnehilmann/markdeck">Markdeck</a><br/>
GitHub <a href="https://github.com/gerald1248/kubernetes-horcrux-slides">gerald1248/kubernetes-horcrux-slides</a><br/>
Twitter <a href="https://twitter.com/03spirit">@03spirit</a></small>
