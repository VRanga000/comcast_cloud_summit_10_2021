# High-availability {bgcss=janusslide}

<div class="r-stack">
  <div class="fragment fade-in-then-out">
  ```{.render_plantuml}
  @startuml
  !include <kubernetes/k8s-sprites-unlabeled-25pct>

  skinparam linetype line
  skinparam defaultTextAlignment left

  component "<$svc>\nservice" as svc
    node "<$node>\nnode 1" {
      component "<$pod>\npod 1" as p1
      component "<$pod>\npod 2" as p2
      component "<$pod>\npod 3" as p3

      svc ---> p1
      svc ---> p2
      svc ---> p3

    }
  @enduml
  ```
  </div>
</div>

---
