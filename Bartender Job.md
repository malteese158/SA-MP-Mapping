# SAMP-Development
Open source for download



						Bartender System - Edited by Malteese (Vietnamese Version)

				Next Generation Gaming, LLC
	(created by Next Generation Gaming Development Team)
					


CMD:bannuoc(playerid, params[])
{
	if(PlayerInfo[playerid][pJob] == 19 || PlayerInfo[playerid][pJob2] == 19 || PlayerInfo[playerid][pJob3] == 19)
	{
		if(IsAtBar(playerid))
		{
			new string[128], giveplayerid;
			if(sscanf(params, "u", giveplayerid)) return SendClientMessageEx(playerid, COLOR_GREY, "USAGE: /bannuoc [player]");

			if(IsPlayerConnected(giveplayerid))
			{
				if(playerid == giveplayerid)
				{
					return SendClientMessageEx(playerid, COLOR_GREY, " Ban khong the ban nuoc cho minh.");
				}
				if (ProxDetectorS(8.0, playerid, giveplayerid))
				{
					DrinkOffer[giveplayerid] = playerid;
					format(string, sizeof(string), "* Bartender %s da de nghi ban mot ly nuoc cho ban. /chapnhan nuoc de chon nuoc uong cua ban.", GetPlayerNameEx(playerid));
					SendClientMessageEx(giveplayerid, COLOR_LIGHTBLUE, string);
					format(string, sizeof(string), "* Ban da de nghi %s mua nuoc.",GetPlayerNameEx(giveplayerid));
					SendClientMessageEx(playerid, COLOR_LIGHTBLUE, string);
				}
				else
				{
					return SendClientMessageEx(playerid, COLOR_GREY, " Nguoi do khong dung gan ban!");
				}
			}
			else
			{
				return SendClientMessageEx(playerid, COLOR_GREY, " Nguoi do khong the mua nuoc cua ban!");
			}
		}
		else
		{
			SendClientMessageEx(playerid, COLOR_GREY, "   Ban khong o quay Bar!");
			return 1;
		}
	}
	else
	{
		SendClientMessageEx(playerid, COLOR_GREY, " Ban khong phai la nhan vien Bartender!");
		return 1;
	}
	return 1;
}
