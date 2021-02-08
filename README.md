# Hit-and-Damage
##Hit
public class PlayerHit : MonoBehaviour, IHittable
 {
     IDamageable damageable;
     
     void Start()
     {
         damageable = (IDamageable)GetComponent(typeof(IDamageable));
         if (damageable == null)
         {
             throw new MissingComponentException("Requires an implementation of IDamageable")
         }
     }
     
     public void Hit()
     {
         damageable.Damage(/*_____________*/);
     }
 }
 ## Damage
 public class PlayerDamage : MonoBehaviour, IDamageable
 {
     Stats stats;
     
     void Start()
     {
         stats = GetComponent<Stats>();
     }
     
     public void Damage(int damageTaken)
     {
         stats.health -= damageTaken;
     }
 }
