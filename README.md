// Buradan aşağı kısmı alınız başında çift slash işareti olan yerleri almanıza gerek yok.
// Get down from here, you don't need to buy places with a double slash sign at the beginning.
// ***************BILGILENDIRME***************
// Police Ceza Kesme /w webhook destekli v1.0
// Created By: Meedic Bear#7111 edited by berk.png#6627
// Eğer herhangi birşey bilmiyor iseniz hiçbir kodu ellemeyiniz.
// ***************BILGILENDIRME***************
 
command cezakes(arg, arg1, arg2){
    permission = "police.cezakes";
    execute(){
        if(isSet(arg) == false){
          player.message("Proper Usage: /cezakes (player) (amount) (reason)", "red");
        }
        else{
            if(isSet(arg1) == false){
              player.message("Proper Usage: /cezakes (player) (amount) (reason)", "red");
            }
            else{
                if(isSet(arg2) == false){
                    player.message("Proper Usage: /cezakes (player) (amount) (reason)", "red");
                }
                else{
                    if(arg1 > 100000){
                        player.message("Fine cannot exceed 100,000", "red");
                    }
                    else{
                      victim = toPlayer(arg);
                      if(isPlayer(victim)){
                        victim.decreaseBalance(arg1);
                        player.increaseBalance(arg1);
                        victim.message("You been fined $" + arg1 + " by " + player.name + "for " + arg2 + "!", "yellow");
                        player.message("You have fined " + victim.name +" $"+ arg1 + "for " + arg2 + "!", "yellow");
                        discord.send("**Fine** | " + player.name + " has fined " + victim.name + arg1 + "for " + arg2 , "CHANGE_ME_WEBHOOK_URL", "Police Fines", "CHANGE_ME_WEBHOOK_ICON");
                      }
                      else{
                        player.message("Could Not Find That Player!", "red");
                      }
                    }
                }
            }
        }
    }
}
