---
title: "方法 : Visual C++ でキーワードを定義する | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ユーザーのキーワード"
  - "予約語、ユーザー定義のキーワード"
  - "ユーザー定義のキーワード"
  - "予約済みのキーワード、ユーザー定義"
  - "usertype.dat"
  - "キーワード [C++]、ユーザー定義"
ms.assetid: 2dfcf343-e861-4bde-b5a4-7deb6773d9c8
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 方法 : Visual C++ でキーワードを定義する
キーワードは、特別な意味を持つ定義済みおよび予約済みの識別子です。 プログラムでは、キーワードを識別子として使用することはできません。 ただし、Visual C\+\+ で使用する独自のキーワードを定義して、カスタマイズされた構文の色分けをキーワードに割り当てることができます。 構文を色分け表示すると、コードの構造および状態に関する視覚的な手掛かりが得られます。  
  
### 独自の Visual C\+\+ のキーワードを定義するには  
  
1.  Visual Studio の[コード エディターとテキスト エディター](http://msdn.microsoft.com/ja-jp/508e1f18-99d5-48ad-b5ad-d011b21c6ab1)か Notepad.exe を使用して、`usertype.dat` という名前のテキストのみのファイルを作成します。  
  
2.  `usertype.dat` で、ユーザー定義のキーワードを別々の行にそれぞれ入力します。  
  
3.  `usertype.dat` を devenv.exe が格納されているディレクトリに保存します。 既定では、そのディレクトリのパスは *\<drive\>*:\\Program Files\\[!INCLUDE[TLA#tla_visualstu](../misc/includes/tlasharptla_visualstu_md.md)] *\<major.minor version number\>*\\Common7\\[!INCLUDE[TLA2#tla_ide](../misc/includes/tla2sharptla_ide_md.md)] です。 このディレクトリは既定では読み取り専用のため、`usertype.dat` を保存するには管理資格情報が必要です。  
  
4.  Visual Studio を終了してから再起動します。  
  
    > [!NOTE]
    >  `usertype.dat` ファイルは初期化時に読み取られるため、編集セッション中はファイル名の変更やファイルの再読み込みはできません。 構文の色分け表示メカニズムは `usertype.dat` ファイルを最後に確認するため、以前に定義されたすべての色分け設定が優先されます。  
  
5.  **\[ツール\]** メニューの **\[オプション\]** をクリックします。**\[オプション\]** ダイアログ ボックスで、**\[環境\]**、**\[フォントおよび色\]** の順にクリックして、**\[アイテムの表示:\]** リストで **\[C\/C\+\+ ユーザー キーワード\]** をクリックします。  
  
6.  [\[フォントおよび色\] \(\[オプション\] ダイアログ ボックス \- \[環境\]\)](../Topic/Fonts%20and%20Colors,%20Environment,%20Options%20Dialog%20Box.md) の説明に従って、ユーザー定義のキーワードのフォントと色のプロパティを設定します。  
  
 詳細については、「[C\+\+ キーワード](/visual-cpp/cpp/keywords-cpp)」を参照してください。  
  
## 参照  
 [ユーザー グループのメンバーとしての実行](/visual-cpp/top/running-as-a-member-of-the-users-group)   
 [既定のキーボード ショートカット](../ide/default-keyboard-shortcuts-in-visual-studio.md)