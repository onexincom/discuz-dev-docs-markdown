# 插件嵌入点列表
· 全局`(common/)`


```php
 extcredits.htm
     string spacecp_credit_extra
 faq.htm
     string faq_extra
 footer.htm
     string global_footer
     string global_footerlink
 header.htm
     string global_cpnav_top (X2.5)
     string global_cpnav_extra1
     string global_cpnav_extra2
     string global_myitem_extra (X3.1)
     string global_qmenu_top (X3)
     string global_qmenu_bottom (X3)
     string global_nav_extra (X2.5)
     string global_header
 userabout.htm
     array global_userabout_top
     string userapp_menu_top
     string userapp_menu_middle
     array global_userabout_bottom
 userstatus.htm
     string global_usernav_extra1
     string global_usernav_extra2
     string global_usernav_extra3
     string global_usernav_extra4 (X2.5)

```
· 论坛`(forum/)`


```php
 collection_all.htm (X2.5)
     string collection_index_top
     string collection_index_bottom
 collection_comment.htm (X2.5)
     string collection_nav_extra
 collection_index.htm (X2.5)
     string collection_index_top
     string collection_index_bottom
 collection_mycollection.htm (X2.5)
     string collection_index_top
     string collection_index_bottom
 collection_nav.htm (X2.5)
     string collection_nav_extra
 collection_view.htm (X2.5)
     string collection_viewoptions
     string collection_view_top
     string collection_threadlistbottom
     string collection_relatedop
     string collection_view_bottom
     string collection_side_bottom
 discuz.htm
     string index_status_extra
     string index_nav_extra (X2.5)
     string index_top
     string index_catlist_top (X2.5)
     array index_followcollection_extra (X3)
     array index_favforum_extra (X2.5)
     array index_favforum_extra (X3)
     array index_catlist (X2.5)
     array index_forum_extra (X2.5)
     array index_forum_extra (X2.5)
     array index_datacollection_extra (X3)
     string index_middle
     string index_bottom
     string index_side_top
     string index_side_bottom
 discuzcode.htm
     array viewthread_attach_extra (X2.5)
 editor_menu_forum.htm
     string post_image_btn_extra
     string post_image_tab_extra
     string post_attach_btn_extra
     string post_attach_tab_extra
 forumdisplay.htm
     string forumdisplay_leftside_top
     string forumdisplay_leftside_bottom
     string forumdisplay_forumaction
     string forumdisplay_modlink
     string forumdisplay_top
     string forumdisplay_middle
     string forumdisplay_postbutton_top
     string forumdisplay_threadtype_inner (X2.5)
     string forumdisplay_filter_extra (X2.5)
     string forumdisplay_threadtype_extra (X2.5)
     string forumdisplay_bottom
     string forumdisplay_side_top
     string forumdisplay_side_bottom
 forumdisplay_fastpost.htm
     string forumdisplay_fastpost_content
     string forumdisplay_fastpost_func_extra
     string forumdisplay_fastpost_ctrl_extra
     string global_login_text
     string forumdisplay_fastpost_upload_extend (X3)
     string forumdisplay_fastpost_btn_extra
     string forumdisplay_fastpost_sync_method
 forumdisplay_list.htm
     string forumdisplay_filter_extra
     array forumdisplay_thread
     array forumdisplay_thread_subject (X2.5)
     array forumdisplay_author
     array forumdisplay_thread (X2.5)
     array forumdisplay_author (X2.5)
     string forumdisplay_threadlist_bottom (X2.5)
     string forumdisplay_postbutton_bottom
 forumdisplay_sort.htm (X2.5)
     string forumdisplay_postbutton_bottom
 forumdisplay_subforum.htm (X2.5)
     array forumdisplay_subforum_extra
     array forumdisplay_subforum_extra
 guide.htm
     string guide_nav_extra
     string guide_top
     string guide_bottom
 index_navbar.htm
     string index_navbar
 post.htm
     string post_top
     string post_middle
     string post_btn_extra
     string post_sync_method
     string post_bottom
     string post_upload_extend (X3)
 post_activity.htm
     string post_activity_extra
 post_debate.htm
     string post_debate_extra
 post_editor_attribute.htm (X3)
     string post_attribute_extra
     string post_attribute_extra_body
 post_editor_body.htm
     string post_editorctrl_right
     string post_editorctrl_left
     string post_editorctrl_top
     string post_editorctrl_bottom
 post_infloat.htm
     string post_infloat_top
     string post_infloat_middle
     string post_infloat_btn_extra
 post_poll.htm
     string post_poll_extra
     string post_poll_upload_extend (X3)
 post_reward.htm
     string post_reward_extra
 post_trade.htm
     string post_trade_extra
 topicadmin_modlayer.htm
     string forumdisplay_modlayer
     string modcp_modlayer
 trade_info.htm
     string viewthread_tradeinfo_extra
 viewthread.htm
     string viewthread_top
     string viewthread_postbutton_top
     string viewthread_modoption
     string viewthread_beginline (X2.5)
     string viewthread_title_extra
     string viewthread_title_row
     string viewthread_middle
     string viewthread_bottom
 viewthread_activity.htm
     string viewthread_activity_extra1
     string viewthread_activity_extra2
 viewthread_album.htm (X3)
     string viewthread_beginline
     string viewthread_useraction_prefix
     string viewthread_useraction
     string viewthread_bottom
 viewthread_fastpost.htm
     string viewthread_fastpost_side
     string viewthread_fastpost_content
     string viewthread_fastpost_func_extra
     string viewthread_fastpost_ctrl_extra
     string global_login_text
     string viewthread_fastpost_upload_extend (X3)
     string viewthread_fastpost_btn_extra (X2.5)
 viewthread_from_node.htm
     array viewthread_postheader
     array viewthread_postheader
     array viewthread_postheader
     array viewthread_endline
 viewthread_node.htm
     array viewthread_profileside
     array viewthread_imicons
     array viewthread_magic_user
     array viewthread_avatar
     array viewthread_sidetop
     array viewthread_sidebottom
     array viewthread_postheader
     string viewthread_modaction (X2.5)
     string viewthread_share_method
     string viewthread_useraction
     array viewthread_postsightmlafter (X2.5)
     array viewthread_postfooter
     array viewthread_postaction (X2.5)
     string viewthread_magic_thread
     array viewthread_magic_post
     array viewthread_endline
 viewthread_node_body.htm
     array viewthread_posttop
     string global_login_text
     array viewthread_postbottom
 viewthread_poll.htm
     string viewthread_poll_top
     string viewthread_poll_bottom
 viewthread_portal.htm
     string viewthread_useraction_prefix
     string viewthread_useraction
     string viewthread_side_bottom
 viewthread_preview_node.htm (X3)
     array viewthread_postheader
     array viewthread_endline
 viewthread_trade.htm
     array viewthread_trade_extra

```
· 群组`(group/)`


```php
 group.htm
     string group_navlink
     string forumdisplay_navlink
     string group_navlink
     string forumdisplay_navlink
     string group_top
     string forumdisplay_top
     string group_nav_extra
     string forumdisplay_nav_extra
     string group_bottom
     string forumdisplay_bottom
     string group_side_bottom
     string forumdisplay_side_bottom
 group_list.htm
     string forumdisplay_postbutton_top
     string forumdisplay_filter_extra
     array forumdisplay_thread
     string forumdisplay_postbutton_bottom
 group_my.htm
     string my_header
     string my_bottom
     string my_side_top
     string my_side_bottom
 group_right.htm
     string group_index_side
     string group_side_top
     string forumdisplay_side_top
 index.htm
     string index_header
     string index_top
     string index_bottom
     string index_side_top
     string index_side_bottom
 type.htm
     string index_top
     array index_grouplist
     string index_bottom
     string index_side_top
     string index_side_bottom

```
· 家园`(home/)`


```php
 editor_image_menu.htm (X3)
     string spacecp_blog_upload_extend
     string portalcp_top_upload_extend
 follow_feed.htm
     string follow_nav_extra
     string follow_top
     string follow_upload_extend (X3)
     string follow_nav_extra (X3)
 spacecp_avatar.htm
     string spacecp_avatar_top
     string spacecp_avatar_bottom
 spacecp_blog.htm
     string spacecp_blog_top
     string spacecp_blog_middle
     string spacecp_blog_bottom
 spacecp_credit_base.htm
     string spacecp_credit_top
     string spacecp_credit_extra
     string spacecp_credit_bottom
 spacecp_credit_log.htm
     string spacecp_credit_top
     string spacecp_credit_bottom
 spacecp_privacy.htm
     string spacecp_privacy_top
     string spacecp_privacy_base_extra
     string spacecp_privacy_feed_extra
     string spacecp_privacy_bottom
 spacecp_profile.htm
     string spacecp_profile_top
     string spacecp_profile_extra
     string spacecp_profile_bottom
 spacecp_promotion.htm
     string spacecp_promotion_top
     string spacecp_promotion_bottom
 spacecp_upload.htm (X3)
     string spacecp_upload_extend
 spacecp_usergroup.htm
     string spacecp_usergroup_top
     string spacecp_usergroup_bottom
     string spacecp_usergroup_top
     string spacecp_usergroup_bottom
     string spacecp_usergroup_top
     string spacecp_usergroup_bottom
 space_album_pic.htm
     string space_album_pic_top
     string space_album_pic_op_extra
     string space_album_pic_bottom
     string space_album_pic_face_extra
 space_album_view.htm
     string space_album_op_extra
 space_blog_list.htm
     array space_blog_list_status
 space_blog_view.htm
     string space_blog_title
     string space_blog_share_method (X2.5)
     string space_blog_op_extra
     string space_blog_face_extra
 space_card.htm
     string space_card_top
     string space_card_baseinfo_middle
     string space_card_baseinfo_bottom
     string space_card_option
     string space_card_magic_user
     string space_card_bottom
 space_comment_li.htm
     array global_space_comment_op (X3)
     string global_comment_bottom (X3)
 space_doing.htm
     string space_doing_top
     string space_doing_bottom
 space_favorite.htm
     string space_favorite_nav_extra
 space_friend.htm
     string space_interaction_extra
 space_header.htm
     string global_usernav_extra1
     string global_usernav_extra2
 space_home.htm
     string space_home_navlink (X3)
     string space_home_side_top (X2.5)
     string space_home_side_bottom
     string space_home_top
     string space_home_navlink
     string space_home_bottom
 space_magic.htm (X2.5)
     string magic_nav_extra
 space_medal.htm (X2.5)
     string medal_nav_extra
 space_menu.htm
     string space_menu_extra
 space_profile_body.htm
     string space_profile_baseinfo_top
     string follow_profile_baseinfo_top (X2.5)
     string space_profile_baseinfo_middle
     string follow_profile_baseinfo_middle (X2.5)
     string space_profile_baseinfo_bottom
     string follow_profile_baseinfo_bottom (X2.5)
     string space_profile_extrainfo
     string follow_profile_extrainfo (X2.5)
 space_share_li.htm
     array space_share_comment_op
 space_status.htm
     string space_home_doing_sync_method
 space_wall.htm
     string space_wall_face_extra

```
· 注册/登录`(member/)`


```php
 login.htm
     string logging_side_top
     string logging_top
     string logging_input
     string logging_method
 login_simple.htm
     string global_login_extra
 register.htm
     string register_side_top
     string register_top
     string register_input
     string register_logging_method
     string register_bottom

```
· 门户`(portal/)`


```php
 portalcp_article.htm
     string portalcp_top
     string portalcp_extend
     string portalcp_middle
     string portalcp_bottom
 view.htm
     string view_article_top (X2.5)
     string view_article_subtitle (X2.5)
     string view_article_summary (X2.5)
     string view_article_content (X2.5)
     string view_share_method
     string view_article_op_extra (X2.5)
     string view_article_side_top (X2.5)
     string view_article_side_bottom (X2.5)

```
· 排行榜`(ranklist/)`


```php
 side_left.htm
     string ranklist_nav_extra

```
· 搜索`(search/)`


```php
 album.htm
     string album_top
     string album_bottom
 blog.htm
     string blog_top
     string blog_bottom
 collection.htm (X3)
     string collection_top
     string collection_bottom
 footer.htm
     string global_footer
     string global_footerlink
 forum.htm
     string forum_top
     string forum_bottom
 group.htm
     string group_top
     string group_bottom
 header.htm
     string global_usernav_extra1
     string global_usernav_extra2
 portal.htm
     string portal_top
     string portal_bottom

```
· 应用`(userapp/)`


```php
 userapp_app.htm
     string userapp_app_top
     string userapp_app_bottom
 userapp_index.htm
     string userapp_index_top
     string userapp_index_bottom
 userapp_menu_list.htm
     string userapp_menu_top
     string userapp_menu_middle
     string userapp_menu_bottom

```
· 手机标准版`(mobile/common/)`


```php
 footer.htm
     string global_footer_mobile
 header.htm
     string global_header_mobile

```
· 手机标准版`(mobile/forum/)`


```php
 discuz.htm
     string index_top_mobile
     string index_middle_mobile
     string index_bottom_mobile
 forumdisplay.htm
     string forumdisplay_top_mobile
     array forumdisplay_thread_mobile
     string forumdisplay_bottom_mobile
 viewthread.htm
     string viewthread_top_mobile
     array viewthread_posttop_mobile
     array viewthread_postbottom_mobile
     string viewthread_bottom_mobile

```
· 手机触屏版`(touch/common/)`


```php
 footer.htm
      string global_footer_mobile
  header.htm
      string global_header_mobile

```
· 手机触屏版`(touch/forum/)`


```php
 discuz.htm
      string index_top_mobile
      string index_middle_mobile
  forumdisplay.htm
      string forumdisplay_top_mobile
      array forumdisplay_thread_mobile
      string forumdisplay_bottom_mobile
  forumdisplay_fastpost.htm
      string viewthread_fastpost_button_mobile (X3.1)
  post.htm
      string post_bottom_mobile (X3.1)
  viewthread.htm
      string viewthread_top_mobile
      array viewthread_posttop_mobile
      array viewthread_postbottom_mobile
      string viewthread_bottom_mobile

```
· 手机触屏版`(touch/member/)`


```php
 login.htm
      string logging_bottom_mobile (X3.1)

```
· 手机极简版`(wml/forum/)`


```php
 discuz.htm
     string index_top_mobile
     string index_middle_mobile
 forumdisplay.htm
     string forumdisplay_top_mobile
     array forumdisplay_thread_mobile
     string forumdisplay_bottom_mobile
 viewthread.htm
     string viewthread_top_mobile
     array viewthread_posttop_mobile
     array viewthread_postbottom_mobile
     string viewthread_bottom_mobile

```
更新时间：2013-9-3

