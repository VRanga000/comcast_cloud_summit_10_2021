# Traffic shaping {bgcss=janusslide}

<div class="r-stack">
<div class="fragment fade-in-then-out">
Never upgrade a live cluster
</div>

<div class="fragment fade-in-then-out">
Shift traffic from old cluster to new
</div>


<div class="fragment">
  ```{.render_plantuml}
  @startuml
  !include <kubernetes/k8s-sprites-unlabeled-25pct>

  skinparam linetype line
  skinparam defaultTextAlignment left

  note "live production facing services" as n1
  note "identical cluster not facing production traffic" as n2
  package "active cluster" as p1 {
      component "<$svc>\nservice A" as s1
      component "<$svc>\nservice B" as s2
      component "<$svc>\nservice C" as s3
  }
  package "passive cluster" as p2 {
      component "<$svc>\nservice A" as s4
      component "<$svc>\nservice B" as s5
      component "<$svc>\nservice C" as s6
  }

  n1 .. p1
  n2 .. p2
  @enduml
  ```
</div>
</div>
