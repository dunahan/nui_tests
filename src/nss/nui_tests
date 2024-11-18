#include "nw_inc_nui"
#include "nw_inc_nui_insp"

const string NUI_WINDOW_BUFFWATCHER = "BuffWatcherWindow";

void main()
{
  object oPC = GetFirstPC();

  //following the base config of the window
  json jGeometry = NuiRect(-1.0f, -1.0f, 200.0f, 100.0f);   //geometry and placing of the window
  json jResize = JsonBool(TRUE);                            //is it resizeable
  json jCollapse = JsonNull();                              //collapseable (JsonNull() == Users liking)
  json jClose = JsonBool(TRUE);                             //closeable
  json jTransparent = JsonBool(TRUE);                       //background
  json jBorder = JsonBool(TRUE);                            //border
  json jResRef = JsonString(Get2DAString("spells", "IconResRef" , 100));

  //add one widget to get it running
  json jBaseOptions = NuiImage(jResRef, JsonInt(NUI_ASPECT_EXACT), JsonInt(NUI_HALIGN_LEFT), JsonInt(NUI_VALIGN_TOP));  //add one spell pic (light) as image
       jBaseOptions = NuiHeight(jBaseOptions, 32.0f);  //the nui_img should only be 32x32 and should not resize with the window
       jBaseOptions = NuiWidth(jBaseOptions, 32.0f);
       jBaseOptions = NuiTooltip(jBaseOptions, JsonString("Test")); //add a test tooltip

  // now build the window with its widgets
  json jRoot = JsonArray();                                 //base of Nui Window
  json jRow = JsonArray();                                  //base where to put Widgets (Buttons, Labels aso)
       jRow = JsonArrayInsert(jRow, jBaseOptions);          //insert one Button for options

       jRow = NuiRow(jRow);                                 //end the creation and give the base Nui a form

       jRoot = JsonArrayInsert(jRoot, jRow);                //add the row to the root base
       jRoot = NuiCol(jRoot);                               //give the root a form

  //this will be the window
  json jNui = NuiWindow(jRoot, JsonString("Active Buffs"), jGeometry, jResize, jCollapse, jClose, jTransparent, jBorder);  // build the window

  // we create it now
  int nToken = NuiCreate(oPC, jNui, NUI_WINDOW_BUFFWATCHER);  // and show it to the user

  SendMessageToPC(oPC, IntToString(nToken));
}
