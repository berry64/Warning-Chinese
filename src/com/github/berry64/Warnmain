package com.github.berry64;

import java.io.File;

import org.bukkit.Bukkit;
import org.bukkit.ChatColor;
import org.bukkit.command.Command;
import org.bukkit.command.CommandSender;
import org.bukkit.command.ConsoleCommandSender;
import org.bukkit.entity.Player;
import org.bukkit.plugin.java.JavaPlugin;

public class Warnmain extends JavaPlugin{
	@Override
	public void onEnable(){
		getLogger().info("警告插件已启动!");
		CreateConfig();
	}
	public boolean onCommand(CommandSender sender, Command cmd, String label, String[] args){
		if(cmd.getName().equalsIgnoreCase("warn")){
			if(sender.hasPermission("warn.warn")){
				if (args.length != 2){
					sender.sendMessage(ChatColor.RED+ "请使用/warn [玩家] [原因]");
				}
				else{
					Player target = (Bukkit.getServer().getPlayer(args[0]));
					if(target == null){
						sender.sendMessage(ChatColor.AQUA+ args[0]+"不存在");
					}
					else{
						sendmessage(args[0], args[1]);
						sender.sendMessage(ChatColor.YELLOW+"已向玩家"+ args[0] +"发送警告, 原因:"+ ChatColor.GREEN+ args[1]);
					}
				}
			}
		}
		return true;
	}
	public void CreateConfig(){
		if (!new File(getDataFolder() + File.separator + "config.yml").exists()) {
			saveDefaultConfig();
			say(ChatColor.YELLOW + "无法找到config.yml,正在创建");
		} try {
			reloadConfig();
			say(ChatColor.YELLOW + "成功加载config");
		} catch (Exception e) {
			e.printStackTrace();
 	      getServer().getPluginManager().disablePlugin(this);
 	      say(ChatColor.RED + "无法读取config");
		}
	}
	public void say(String s){
		ConsoleCommandSender sender = Bukkit.getConsoleSender();
		sender.sendMessage(s);
	}
	public void sendmessage(String p, String m){
		Player asdf = (Bukkit.getServer().getPlayer(p));
		asdf.sendMessage(ChatColor.DARK_GRAY+"=========================");
		asdf.sendMessage((getConfig().getString("Warn_message").replaceAll("<reason>", m).replaceAll("&", "§")));
		asdf.sendMessage(ChatColor.DARK_GRAY+"=========================");
	}
}
