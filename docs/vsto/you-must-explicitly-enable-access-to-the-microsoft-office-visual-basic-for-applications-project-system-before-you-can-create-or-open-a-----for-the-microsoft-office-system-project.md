---
title: "Visual Studio Tools for the Microsoft Office System プロジェクトを作成または開く前に、Microsoft Office Visual Basic for Applications プロジェクト システムへのアクセスを明示的に有効にしなければなりません。 | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vst.project.vbawrongversion"
  - "VST.Project.VBASecurityGenericError"
  - "VST.Project.VBASecurityPermissions"
  - "VST.SelectDocWizard.MissingCOM"
  - "VST.Project.VBASecurityNotSet"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: 538021e6-1776-453d-9899-d7fca2f1f58f
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 18
---
# Visual Studio Tools for the Microsoft Office System プロジェクトを作成または開く前に、Microsoft Office Visual Basic for Applications プロジェクト システムへのアクセスを明示的に有効にしなければなりません。
  Office 開発プロジェクトは、プロジェクトで Visual Basic for Applications を使用しない場合でも、Microsoft Office Word や Microsoft Office Excel の Visual Basic for Applications プロジェクト システムにアクセスする必要があります。  Visual Basic プロジェクトと C\# プロジェクトでは、デザイン時にコントロールをサポートするために Visual Basic for Applications プロジェクト システムを使用します。  
  
 一部の Microsoft Office マクロ ウイルスは、ウイルス感染を広げる手段として Visual Basic for Applications プロジェクト システムを自動化しようとします。  Visual Basic for Applications プロジェクト システムへのアクセスを許可すると、マクロ ウイルスの感染防止に有効な保護手段が削除されます。  ただし、通常のマクロ セキュリティは有効なままであるため、コンピューターでマクロを実行するかどうかは、Office アプリケーションで保持されているマクロ セキュリティ レベルおよび信頼される発行者のリストによって決まります。  
  
> [!NOTE]  
>  これは開発用のコンピューターにのみ適用されます。  エンド ユーザーのコンピューターでは、Office ソリューションを実行するためにこのオプションを有効にする必要はありません。  
  
 Visual Basic for Applications プロジェクト システムへのアクセスを禁止してもウイルスから保護されないことに注意してください。コンピューターがそれ以前に一部のマクロ ウイルスに感染していた場合にも、他の文書へのウイルス感染の防止に役立つだけです。  コンピューターに保護層を追加するこのオプションは、既定では無効になっていますが、セキュリティに関する以下のベスト プラクティスに従えば、このオプションを有効にしてもコンピューターがウイルスに感染しやすくなることはありません。  
  
 Office のマクロ ウイルスに対する最善の保護対策は、セキュリティ レベルを「高」または「最高」に設定して Office を実行し、検証された既知のソースのマクロのみを信頼し、常にセキュリティ パッチとウイルス検出プログラムを最新にしておくことです。  
  
 ウイルスおよびその他の悪意のあるコードから PC を保護する方法の詳細については、[http:\/\/www.microsoft.com\/protect](http://www.microsoft.com/protect) を参照してください。  
  
 **\[Visual Basic プロジェクトへのアクセスを信頼する\]** オプションは手動で有効または無効にできます。  
  
 VBA エラーまたは COM エラーが表示される場合、Office のインストールを修復できます。  
  
### Visual Basic プロジェクトへのアクセスを有効または無効にするには  
  
1.  Word または Excel の **\[ツール\]** メニューで **\[マクロ\]** をポイントし、**\[セキュリティ\]** をクリックします。  
  
2.  **\[セキュリティ\]** ダイアログ ボックスで **\[信頼できる発行元\]** タブをクリックします。  
  
3.  **\[Visual Basic プロジェクトへのアクセスを信頼する\]** を有効にするにはオンにして、無効にするにはオフにします。  
  
4.  **\[OK\]** をクリックします。  
  
### Office マクロのセキュリティ レベルを設定するには  
  
1.  Word または Excel の **\[ツール\]** メニューで **\[マクロ\]** をポイントし、**\[セキュリティ\]** をクリックします。  
  
2.  **\[セキュリティ レベル\]** タブで必要な設定を選択します。  
  
     **\[セキュリティ レベル\]** タブには、各レベルの詳細な設定が含まれています。  詳細については、Office ヘルプの「マクロのセキュリティ レベル」を参照してください。  
  
### 2007 Microsoft Office システムとともに VBA をインストールするには  
  
1.  コントロール パネルで**\[プログラムの追加と削除\]** または **\[プログラムと機能\]** を実行します。  
  
2.  **\[現在インストールされているプログラム\]** リストで \[Office\] を選択します。  
  
3.  **\[変更\]** をクリックします。  
  
4.  **\[機能の追加または削除\]** を選択して **\[続行\]** をクリックします。  
  
5.  **\[アプリケーションごとにオプションを指定してインストール\]** を選択して **\[次へ\]** をクリックします。  
  
6.  **\[アプリケーションおよびツールの更新オプションの選択\]** リストの **\[Office 共有機能\]** を展開します。  
  
7.  **\[Visual Basic for Applications\]** の横にあるドロップダウン メニューを開き、**\[マイ コンピューターから実行\]** をクリックします。  
  
8.  **\[続行\]** をクリックします。  
  
9. **\[閉じる\]** をクリックします。  
  
### Office のインストールを修復するには  
  
1.  コントロール パネルで**\[プログラムの追加と削除\]** または **\[プログラムと機能\]** を実行します。  
  
2.  **\[現在インストールされているプログラム\]** リストで、Office の使用しているバージョンを選択します。  
  
3.  **\[変更\]** をクリックします。  
  
4.  **\[再インストール\/修復\]** を選択し、**\[次へ\]** をクリックします。  
  
5.  **\[Office のインストールで発生したエラーを検出して修復する\]** を選択して **\[インストール\]** をクリックします。  
  
## 参照  
 [Office ソリューションのセキュリティ保護](../vsto/securing-office-solutions.md)  
  
  