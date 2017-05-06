---
title: "方法: Visual Studio で Office プロジェクトを作成する"
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
  - "VST.SelectDocWizard.Page1"
  - "VST.SelectDocWizard.Http"
  - "VST.SelectDocWizard.Extension"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "アドイン [Visual Studio での Office 開発], 作成 (プロジェクトを)"
  - "アプリケーション レベルのアドイン [Visual Studio での Office 開発], 作成 (プロジェクトを)"
  - "ドキュメント レベルのカスタマイズ [Visual Studio での Office 開発], 作成"
  - "Office アプリケーション [Visual Studio での Office 開発], 作成"
  - "Office プロジェクト [Visual Studio での Office 開発]"
  - "プロジェクト [Visual Studio での Office 開発], 作成"
ms.assetid: 0037dbd8-0d2a-4766-90ea-81c819379582
caps.latest.revision: 96
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 95
---
# 方法: Visual Studio で Office プロジェクトを作成する
  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] を使用すると、Microsoft Office アプリケーション向けに、VSTO アドインの作成やドキュメント レベルのカスタマイズができます。 これらの種類のプロジェクトの詳細については、「[Office ソリューションの開発の概要 &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)」を参照してください。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### VSTO アドイン プロジェクトを作成するには  
  
1.  **\[ファイル\]** メニューで、**\[新規\]**、**\[プロジェクト\]** をクリックします。  統合開発環境 \(IDE: Integrated Development Environment\) が [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] 開発設定を使用するように設定されている場合は、**\[ファイル\]** メニューの **\[新規作成\]**、**\[プロジェクト\]** の順に選択します。  
  
     **\[新しいプロジェクト\]** ダイアログ ボックスが表示されます。  
  
    > [!NOTE]  
    >  既定では、Office プロジェクトは [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] を対象とします。  詳細については、「[.NET Framework Client Profile](../Topic/.NET%20Framework%20Client%20Profile.md)」を参照してください。  
  
2.  \[テンプレート\] ペインで、使用する言語のノードの下にある **\[Office\/SharePoint\]** を展開します。  
  
3.  **\[Office アドイン\]** ノードを選択します。  
  
4.  プロジェクト テンプレートの一覧で、VSTO アドイン プロジェクト テンプレートを選択します。  使用できる VSTO アドイン プロジェクト テンプレートの一覧については、「[Office プロジェクト テンプレートの概要](../vsto/office-project-templates-overview.md)」を参照してください。  
  
    > [!NOTE]  
    >  **\[Office アドイン\]** ノードを選択してもプロジェクト テンプレートが表示されない場合、ダイアログ ボックス上部のコンボ ボックスで **\[.NET Framework 4\]** またはそれ以降が選択されていることを確認してください。  Office プロジェクト テンプレートは、.NET Framework の両方のバージョンで表示されます。  
  
5.  **\[名前\]** ボックスにプロジェクト名を入力します。  既定では、このプロジェクト名がソリューション名としても使用されます。  
  
6.  **\[場所\]** ボックスに、プロジェクトを作成する場所を表すパスを入力します。  絶対パスと UNC \(Universal Naming Convention\) パスを使用できます。  HTTP、FTP、またはその他のプロトコル パスは使用しないでください。  
  
     場所は、次の形式で指定します。  
  
    -   \[*drive*\]:\\  
  
    -   \\\\*Server*\\*Share*  
  
     次の文字は使用しないでください。  
  
    -   アスタリスク \(\*\)  
  
    -   縦棒 \(|\)  
  
    -   コロン \(:\) \(ドライブ文字の後に使用する場合は除く\)  
  
    -   二重引用符 \("\) \(スペースを含むパスには引用符は不要\)  
  
    -   小なり \(\<\)  
  
    -   大なり \(\>\)  
  
    -   疑問符 \(?\)  
  
    -   パーセント記号 \(%\)  
  
7.  **\[OK\]** を選択します。  
  
    > [!NOTE]  
    >  アドイン プロジェクトを作成すると、必ず保存されます。  アドイン プロジェクトを一時プロジェクトとして作成することはできません。  一時プロジェクトの詳細については、「[一時プロジェクト](http://msdn.microsoft.com/ja-jp/9cf1944c-7045-44cc-8701-7b0eb4099f2b)」を参照してください。  
  
### ドキュメント レベルのカスタマイズ プロジェクトを作成するには  
  
1.  **\[ファイル\]** メニューで、**\[新規\]**、**\[プロジェクト\]** をクリックします。  IDE が Visual Basic 開発設定を使用するように設定されている場合は、**\[ファイル\]** メニューの **\[新規作成\]**、**\[プロジェクト\]** の順に選択します。  
  
     **\[新しいプロジェクト\]** ダイアログ ボックスが表示されます。  
  
    > [!NOTE]  
    >  既定では、Office プロジェクトは [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] を対象とします。  詳細については、「[.NET Framework Client Profile](../Topic/.NET%20Framework%20Client%20Profile.md)」を参照してください。  
  
2.  \[テンプレート\] ペインで、使用する言語のノードの下にある **\[Office\/SharePoint\]** を展開します。  
  
3.  **\[Office アドイン\]** ノードを選択します。  
  
4.  プロジェクト テンプレートの一覧で、ドキュメント レベルのプロジェクト テンプレートを選択します。  使用できるドキュメント レベルのプロジェクト テンプレートの一覧については、「[Office プロジェクト テンプレートの概要](../vsto/office-project-templates-overview.md)」を参照してください。  
  
    > [!NOTE]  
    >  **\[Office アドイン\]** ノードを選択してもプロジェクト テンプレートが表示されない場合、ダイアログ ボックス上部のコンボ ボックスで **\[.NET Framework 4\]** またはそれ以降が選択されていることを確認してください。  Office プロジェクト テンプレートは、.NET Framework の両方のバージョンで表示されます。  
  
5.  **\[名前\]** ボックスにプロジェクト名を入力します。  既定では、この名前がドキュメントにも使用されます。  IDE が Visual C\# 開発設定または一般的な開発設定を使用するように設定されている場合は、場所とソリューション名も入力します。  
  
    > [!NOTE]  
    >  プロジェクトの場所へのパス、またはプロジェクト名には、サロゲート文字を使用できません。  サロゲート文字の詳細については、「[NIB: Unicode Support for Surrogate Pairs and Combining Character Sequences](http://msdn.microsoft.com/ja-jp/cba3285c-7b47-4ce8-8970-f48d6ac03e39)」を参照してください。  また、オフラインで使用するソリューションを配置する場合は、プロジェクト名に HTTP プロトコルの仕様に準拠した文字を使用する必要があります。  
  
6.  **\[OK\]** を選択します。  
  
     **Visual Studio Tools for Office プロジェクト ウィザード**が開きます。  
  
7.  ソリューションのドキュメントを新規に作成する場合は、**\[新規ドキュメントの作成\]** をクリックします。既存のドキュメントをカスタマイズする場合は、**\[既存のドキュメントをコピーする\]** をクリックします。  
  
     新しいドキュメントを作成する場合は、**\[名前\]** ボックスに名前を指定し、**\[形式\]** ボックスを使用してドキュメントの形式を選択します。  使用できる形式の詳細については、「[ドキュメント レベルのカスタマイズのアーキテクチャ](../vsto/architecture-of-document-level-customizations.md)」を参照してください。  
  
     既存のドキュメントを使用する場合は、**\[既存のドキュメントの完全パス\]** ボックスでドキュメントの場所を指定します。  使用できるパスは、絶対パスと UNC パスです。  ドキュメントへの HTTP パス、FTP パス、または他のプロトコル パスは使用しないでください。  
  
     場所は、次の形式で指定します。  
  
    -   \[*drive*\]:\\  
  
    -   \\\\*Server*\\*Share*  
  
     次の文字は使用しないでください。  
  
    -   アスタリスク \(\*\)  
  
    -   縦棒 \(|\)  
  
    -   コロン \(:\) \(ドライブ文字の後に使用する場合は除く\)  
  
    -   二重引用符 \("\) \(スペースを含むパスには引用符は不要\)  
  
    -   小なり \(\<\)  
  
    -   大なり \(\>\)  
  
    -   疑問符 \(?\)  
  
    -   パーセント記号 \(%\)  
  
    > [!NOTE]  
    >  [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] プロジェクトで既存のドキュメントを使用する場合は、[!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] で作成したドキュメントか、この形式に変換したドキュメントだけを使用してください。  同様に、Word 2010 プロジェクトで既存のドキュメントを使用する場合は、Word 2010 で作成したドキュメントか、Word 2010 に変換したドキュメントだけを使用してください。  以前のバージョンの Word で作成した文書を使用すると、文書の一部の機能が使用できなくなります。  このような機能を使用するコードを記述しようとすると、プロジェクトでエラーが発生する可能性があります。  ドキュメントを変換するには、[!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] または Word 2010 でドキュメントを開き、リボンの **\[ファイル\]** タブで、**\[情報\]**、**\[変換\]** の順に選択します。  
  
8.  **\[完了\]** をクリックします。  
  
9. 次の場合、Word のセキュリティ センターにある信頼できる場所の一覧に、プロジェクト フォルダーとそのサブフォルダーを追加します。  
  
    -   .docm ファイルに基づく Word ドキュメントを作成する、および Windows フォーム コントロールをホストする VBA プロジェクトを含むドキュメントを作成する。  プロジェクト フォルダーを信頼できる場所の一覧に追加すると、デザイン時に文書が期待どおりに動作するか確認するのに役立ちます。  
  
    -   .dotx ファイルに基づく Word テンプレート プロジェクトを作成する。  プロジェクトを実行およびデバッグできるようにするために、プロジェクト フォルダーを信頼できる場所の一覧に追加する必要があります。  
  
     ドキュメントを信頼できる場所の一覧に追加する方法の詳細については、Microsoft Office Online Web サイトの「[ファイルに対して信頼できる場所を作成、削除、変更する](https://support.office.com/ja-jp/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62)」を参照してください。  
  
## 参照  
 [Office プロジェクト テンプレートの概要](../vsto/office-project-templates-overview.md)   
 [Office ソリューションの共同開発](../vsto/collaborative-development-of-office-solutions.md)   
 [Office ソリューションのデザインと作成](../vsto/designing-and-creating-office-solutions.md)   
 [VSTO アドインのプログラミングについて](../vsto/getting-started-programming-vsto-add-ins.md)  
  
  