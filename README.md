# rime_setting_template
Linux fcitx下Rime设置的一个实例(包括导入个人积累词库和其它输入法词库)

A. 导入其它输入法的词库(非用户积累的词). 这里不能用rime_dict_manager, 否则之后Rime会错乱.

以下4个文件包括了一个简单的导入其它输入法词库的过程:
1. default.custom.yaml -- 必须, 同时含有一小部分针对linux的tweak;
2. luna_pinyin.custom.yaml -- 必须, 32行指定了luna_pinyin.extended, 就是指向下面的luna_pinyin.extended.dict.yaml;
3. luna_pinyin.extended.dict.yaml -- 必须, 在26行指定了词库文件是luna_pinyin.sogou.dict.yaml, 可以根据需要增加;
4. luna_pinyin.sogou.dict.yaml -- 这个文件就是要导入的词库, 包含要导入的词语列表. 注意汉字是繁体的, 从其他输入法复制来的一般是简体, 需要opencc转换成繁体 (具体可以去google深蓝词库转换和opencc的用法);
    
把以上4个文件放入~/.config/fcitx/rime, 删除default.yaml以触发下次启动时的重新部署, 重启fcitx. 至此Rime导入其它输入法词库完成.
P.s. 不推荐盲目导入其它输入法的所有词库, 很多词汇其实都用不到, 最好是到某个输入法词库页面看看哪些细胞词库最需要,按需下载导入.

B. 个人词库导入导出则可以用rime_dict_manager, 在debian中apt-get install fcitx-rime后系统即有这个命令.
1. Goto fcitx 配置窗口, 在addon窗口去掉勾选的rime, 重启fcitx;
2. cd ~/.config/fcitx/rime
3. 导出: rime_dict_manager -e luna_pinyin BakupFileName #BakupFileName为要导出的文件名;
4. 导入: rime_dict_manager -i luna_pinyin BakupFileName #BakupFileName为刚才导出的文件名;
5. Goto fcitx 配置窗口, 在addon窗口勾选rime, 重启fcitx;
