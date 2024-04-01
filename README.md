# LerpingRigWeight

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.Animations.Rigging;

public class Lerping : MonoBehaviour
{
    [SerializeField] private float start;
    [SerializeField] private float end;
    [SerializeField] private float waitTime = 0.5f;

    public Rig rig;
    public void StartSmoothRig() => StartCoroutine("SmoothRigEnter");
    public void EndSmoothRig() => StartCoroutine("SmoothRigExit");

    IEnumerator SmoothRigEnter()
    {
        float elapsedTime = 0;
        while (elapsedTime < waitTime)
        {
            rig.weight = Mathf.Lerp(start, end, (elapsedTime / waitTime));
            elapsedTime += Time.deltaTime;
            yield return null;
        }
    }
    IEnumerator SmoothRigExit()
    {
        float elapsedTime = 0;
        while (elapsedTime < waitTime)
        {
            rig.weight = Mathf.Lerp(end, start, (elapsedTime / waitTime));
            elapsedTime += Time.deltaTime;
            yield return null;
        }
    }
}
```
