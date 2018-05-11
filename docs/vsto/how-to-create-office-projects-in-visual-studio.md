---
title: '方法: Visual Studio で Office プロジェクトを作成 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.SelectDocWizard.Page1
- VST.SelectDocWizard.Http
- VST.SelectDocWizard.Extension
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], creating projects
- Office applications [Office development in Visual Studio], creating
- Office projects [Office development in Visual Studio]
- projects [Office development in Visual Studio], creating
- document-level customizations [Office development in Visual Studio], creating
- application-level add-ins [Office development in Visual Studio], creating projects
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 50739bfde7578a49226e5396c8eeb78e56c4b0ae
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-office-projects-in-visual-studio"></a>方法: Visual Studio で Office プロジェクトを作成する
  使用することができます[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]VSTO アドインとドキュメント レベルの作成に Microsoft Office アプリケーション用のカスタマイズ。 この種のプロジェクトの詳細については、次を参照してください。 [Office ソリューション開発の概要&#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)です。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-vsto-add-in-project"></a>VSTO アドイン プロジェクトを作成するには  
  
1.  **[ファイル]** メニューで、 **[新規]**、 **[プロジェクト]**をクリックします。 使用するかどうか、統合開発環境 (IDE) を設定[!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]開発設定の**ファイル**] メニューの [選択**新規**、**プロジェクト**です。  
  
     **[新しいプロジェクト]** ダイアログ ボックスが表示されます。  
  
    > [!NOTE]  
    >  既定では、Office プロジェクトは [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] を対象とします。 詳細については、「[.NET Framework Client Profile](/dotnet/framework/deployment/client-profile)」を参照してください。  
  
2.  展開テンプレート ペインを使用する言語のノードの下で**Office/sharepoint**です。  
  
3.  選択、 **Office アドイン**ノード。  
  
4.  プロジェクト テンプレートの一覧で、VSTO アドイン プロジェクト テンプレートを選択します。 使用できる VSTO アドイン プロジェクト テンプレートの一覧は、次を参照してください。 [Office プロジェクト テンプレートの概要](../vsto/office-project-templates-overview.md)です。  
  
    > [!NOTE]  
    >  選択してもプロジェクト テンプレートが表示されない場合、 **Office アドイン**ノード、ことを確認して**.NET Framework 4**後では、コンボ ボックスで選択 ダイアログ ボックスの上部にあるか。 Office プロジェクト テンプレートは、.NET Framework の両方のバージョンで表示されます。  
  
5.  **名前**ボックスで、プロジェクトの名前を入力します。 既定では、このプロジェクト名がソリューション名としても使用されます。  
  
6.  **場所**ボックスで、プロジェクトを作成するパスを入力します。 絶対パスと UNC (Universal Naming Convention) パスを使用できます。 HTTP、FTP、またはその他のプロトコル パスは使用しないでください。  
  
     場所は、次の形式で指定します。  
  
    -   [*ドライブ*\]: \  
  
    -   \\\\*サーバー*\\*共有*  
  
     次の文字は使用しないでください。  
  
    -   アスタリスク (*)  
  
    -   縦棒 (|)  
  
    -   コロン (:) (ドライブ文字の後に使用する場合は除く)  
  
    -   二重引用符 (") (スペースを含むパスには引用符は不要)  
  
    -   小さい (\<)  
  
    -   大なり (>)  
  
    -   疑問符 (?)  
  
    -   パーセント記号 (%)  
  
7.  **[OK]** を選択します。  
  
    > [!NOTE]  
    >  アドイン プロジェクトを作成すると、必ず保存されます。 アドイン プロジェクトを一時プロジェクトとして作成することはできません。 一時プロジェクトの詳細については、次を参照してください。[一時プロジェクト](http://msdn.microsoft.com/en-us/9cf1944c-7045-44cc-8701-7b0eb4099f2b)です。  
  
### <a name="to-create-a-document-level-customization-project"></a>ドキュメント レベルのカスタマイズ プロジェクトを作成するには  
  
1.  **[ファイル]** メニューで、 **[新規]**、 **[プロジェクト]**をクリックします。 IDE が Visual Basic 開発設定を使用して、に設定されているかどうか、**ファイル**] メニューの [選択**新規**、**プロジェクト**です。  
  
     **[新しいプロジェクト]** ダイアログ ボックスが表示されます。  
  
    > [!NOTE]  
    >  既定では、Office プロジェクトは [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] を対象とします。  詳細については、「[.NET Framework Client Profile](/dotnet/framework/deployment/client-profile)」を参照してください。  
  
2.  展開テンプレート ペインを使用する言語のノードの下で**Office/sharepoint**です。  
  
3.  **[Office アドイン]** ノードを選択します。  
  
4.  プロジェクト テンプレートの一覧で、ドキュメント レベルのプロジェクト テンプレートを選択します。 使用可能なドキュメント レベルのプロジェクト テンプレートの一覧は、次を参照してください。 [Office プロジェクト テンプレートの概要](../vsto/office-project-templates-overview.md)です。  
  
    > [!NOTE]  
    >  選択してもプロジェクト テンプレートが表示されない場合、 **Office アドイン**ノード、ことを確認して**.NET Framework 4**後では、コンボ ボックスで選択 ダイアログ ボックスの上部にあるか。 Office プロジェクト テンプレートは、.NET Framework の両方のバージョンで表示されます。  
  
5.  **名前**ボックスで、プロジェクトの名前を入力します。 既定では、この名前がドキュメントにも使用されます。 IDE が Visual C# 開発設定または一般的な開発設定を使用するように設定されている場合は、場所とソリューション名も入力します。  
  
    > [!NOTE]  
    >  プロジェクトの場所へのパス、またはプロジェクト名には、サロゲート文字を使用できません。 また、オフラインで使用するソリューションを配置する場合は、プロジェクト名に HTTP プロトコルの仕様に準拠した文字を使用する必要があります。  
  
6.  **[OK]** を選択します。  
  
     **Visual Studio Tools for Office プロジェクト ウィザード** が開きます。  
  
7.  選択**新しいドキュメントを作成する**ソリューション用の新しい文書を作成または選択するかどうか**ドキュメントをコピーする既存**を既存のドキュメントをカスタマイズする場合。  
  
     新しいドキュメントを作成する場合に名前を指定、**名前**ボックスし、ドキュメントの形式を使用して、**形式**ボックス。 使用可能な形式の詳細については、次を参照してください。[ドキュメント レベルのカスタマイズのアーキテクチャ](../vsto/architecture-of-document-level-customizations.md)です。  
  
     既存のドキュメントを使用する場合は、ドキュメントの場所を指定、**既存のドキュメントの完全なパス**ボックス。 使用できるパスは、絶対パスと UNC パスです。 ドキュメントへの HTTP パス、FTP パス、または他のプロトコル パスは使用しないでください。  
  
     場所は、次の形式で指定します。  
  
    -   [*ドライブ*\]: \  
  
    -   \\\\*サーバー*\\*共有*  
  
     次の文字は使用しないでください。  
  
    -   アスタリスク (*)  
  
    -   縦棒 (|)  
  
    -   コロン (:) (ドライブ文字の後に使用する場合は除く)  
  
    -   二重引用符 (") (スペースを含むパスには引用符は不要)  
  
    -   小さい (\<)  
  
    -   大なり (>)  
  
    -   疑問符 (?)  
  
    -   パーセント記号 (%)  
  
    > [!NOTE]  
    >  [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] プロジェクトで既存のドキュメントを使用する場合は、[!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] で作成したドキュメントか、この形式に変換したドキュメントだけを使用してください。 同様に、Word 2010 プロジェクトで既存のドキュメントを使用する場合は、Word 2010 で作成したドキュメントか、Word 2010 に変換したドキュメントだけを使用してください。 以前のバージョンの Word で作成した文書を使用すると、文書の一部の機能が使用できなくなります。 このような機能を使用するコードを記述しようとすると、プロジェクトでエラーが発生する可能性があります。 ドキュメントを変換するで開く[!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)]または Word 2010 で、**ファイル**リボン タブで、選択**情報**、**変換**です。  
  
8.  **[完了]** を選択します。  
  
9. 次の場合、Word のセキュリティ センターにある信頼できる場所の一覧に、プロジェクト フォルダーとそのサブフォルダーを追加します。  
  
    -   .docm ファイルに基づく Word ドキュメントを作成する、および Windows フォーム コントロールをホストする VBA プロジェクトを含むドキュメントを作成する。 プロジェクト フォルダーを信頼できる場所の一覧に追加すると、デザイン時に文書が期待どおりに動作するか確認するのに役立ちます。  
  
    -   .dotx ファイルに基づく Word テンプレート プロジェクトを作成する。 プロジェクトを実行およびデバッグできるようにするために、プロジェクト フォルダーを信頼できる場所の一覧に追加する必要があります。  
  
     信頼できる場所にドキュメントを追加する方法の詳細については、Microsoft Office Online web サイトを参照してください。[作成、削除、または変更、ファイルに対して信頼できる場所](https://support.office.com/en-au/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62)です。  
  
## <a name="see-also"></a>関連項目  
 [Office プロジェクト テンプレートの概要](../vsto/office-project-templates-overview.md)   
 [Office ソリューションの共同開発](../vsto/collaborative-development-of-office-solutions.md)   
 [設計と、Office ソリューションの作成](../vsto/designing-and-creating-office-solutions.md)   
 [VSTO アドインのプログラミングについて](../vsto/getting-started-programming-vsto-add-ins.md)  
  
  