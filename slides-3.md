# What is involved in a kubernetes upgrade? {bgcss=janusslide}

<div class="r-stack">
<p class="fragment fade-in-then-out">Control plane (Master nodes)</p>
<div class="fragment fade-in-then-out">
  ```{.render_plantuml}
  @startuml
  !include <kubernetes/k8s-sprites-unlabeled-25pct>

  skinparam linetype line
  skinparam defaultTextAlignment left

  note "Managed by AWS in EKS" as n1
  node "<$node>\nmaster node 1" as master1 {
    component "<$pod>\napi-server" as a1
    component "<$pod>\netcd" as e1
    component "<$pod>\nscheduler" as s1
  }
  node "<$node>\nmaster node 2" as master2 {
    component "<$pod>\napi-server" as a2
    component "<$pod>\netcd" as e2
    component "<$pod>\nscheduler" as s2
  }
  master1 .. n1
  master2 .. n1
  @enduml
  ```
</div>
<p class="fragment fade-in-then-out">Data plane (Worker nodes)</p>
<div class="fragment fade-in-then-out">
![Worker node processes](/assets/worker_node_processes.png)
</div>
<div class="fragment fade-in-then-out">
  ```{.render_plantuml}
  @startuml
  !include <kubernetes/k8s-sprites-unlabeled-25pct>

  skinparam linetype line
  skinparam defaultTextAlignment left

  note "Can be self-managed or managed by AWS in EKS" as n2
  node "<$node>\nworker node 1" as worker1 {
    component "<$pod>\nkubelet" as kubelet1
    component "<$pod>\nkube-proxy" as kp1
  }

  node "<$node>\nworker node 2" as worker2 {
    component "<$pod>\nkubelet" as kubelet2
    component "<$pod>\nkube-proxy" as kp2
  }
  worker1 .. n2
  worker2 .. n2

  @enduml
  ```
</div>
</div>
