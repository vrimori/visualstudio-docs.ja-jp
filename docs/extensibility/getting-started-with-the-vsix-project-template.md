---
title: "VSIX プロジェクト テンプレートの概要 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio SDK, VSIX project template
ms.assetid: 89fac33e-9380-4723-9b45-048a6e16f0ed
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: c87fd485a0d682dc21de21dfe32b83cfc29b520a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="getting-started-with-the-vsix-project-template"></a>VSIX プロジェクト テンプレートの概要
拡張機能を作成するか、展開の既存の拡張機能をパッケージ化する VSIX プロジェクト テンプレートを使用することができます。 VSIX プロジェクト テンプレートは、Visual Basic および Visual c# の両方のバージョンが存在しては、Visual Studio SDK の一部としてインストールします。  
  
 VSIX プロジェクト テンプレートは、拡張機能に関する情報を含む source.extension.vsixmanifest ファイルと出荷資産だけ構成できます。  
  
 VSIX プロジェクト テンプレートを検索するには、Visual Studio SDK をインストールする必要があります。 詳細については、次を参照してください。 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)です。  
  
## <a name="deploying-a-custom-project-template-using-the-vsix-project-template"></a>VSIX プロジェクト テンプレートを使用してカスタム プロジェクト テンプレートを展開します。  
 次の手順では、VSIX プロジェクトを使用して、他の開発者と共有したり、Visual Studio ギャラリーにアップロードできるプロジェクト テンプレートをパッケージ化する方法を示します。  
  
1.  プロジェクト テンプレートを作成します。  
  
    1.  元のテンプレートを作成するプロジェクトを開きます。 このプロジェクトは、任意の種類のプロジェクトすることができます。  
  
    2.  **[プロジェクト]** メニューの **[テンプレートのエクスポート]** をクリックします。 ウィザードの手順を実行します。  
  
         %USERPROFILE%\My documents \visual Studio に .zip ファイルが作成*\<バージョン >*\My エクスポート テンプレート\\です。  
  
2.  空の VSIX プロジェクトを作成します。  
  
     **[ファイル]** メニューの **[新規作成]** をポイントし、 **[プロジェクト]**をクリックします。 いずれかを選択**Visual Basic**または**Visual c#**です。 選択したノードの下にある次のように選択します。 **Extensibility**、し、 **VSIX プロジェクト**です。  
  
3.  .Zip ファイルをプロジェクトに追加します。 設定の**出力ディレクトリにコピー**プロパティを`Copy Always`です。  
  
4.  **ソリューション エクスプ ローラー**をダブルクリックして、`source.extension.vsixmanifest`で開くファイルを**VSIX マニフェスト デザイナー**、次の変更を行います。  
  
    -   設定、 **Product Name**フィールドを**マイ プロジェクト テンプレート**です。  
  
    -   設定、**プロダクト ID**フィールドを**MyProjectTemplate - 1**です。  
  
    -   設定、**作成者**フィールドを**Fabrikam**です。  
  
    -   設定、**説明**フィールドを**マイ プロジェクト テンプレート**です。  
  
    -   **資産**セクションを追加、 **[microsoft.visualstudio.projecttemplate]**を入力し、そのパスの .zip ファイルの名前を設定します。  
  
5.  保存して、source.extension.vsixmanifest ファイルを閉じます。  
  
6.  プロジェクトをビルドします。  
  
7.  出力ディレクトリでは、.vsix ファイルをダブルクリックします。  
  
8.  A **VSIX インストーラー**メッセージ ボックスが表示されます。 拡張機能をインストールする手順に従います。  
  
9. Visual Studio を閉じて再度開きます。  
  
10. 選択**拡張機能と更新プログラム**(上、**ツール**メニュー) を選択し、**テンプレート**カテゴリ。 使用可能な拡張機能の 1 つがあります**マイ プロジェクト テンプレート**です。  
  
11. 新しいプロジェクト テンプレートが表示されます、**新しいプロジェクト**元のプロジェクト テンプレートと同じ場所にダイアログ。 たとえば、という名前のテンプレートを作成した場合**VB コンソール**、Visual Basic コンソール アプリケーションから**VB コンソール**、Visual Basic と同じウィンドウに表示されます**コンソール アプリケーション**テンプレート。  
  
#### <a name="to-specify-the-location-of-the-template-in-the-new-project-dialog-box"></a>[新しいプロジェクト] ダイアログ ボックスで、テンプレートの場所を指定するには  
  
1.  テンプレート フォルダーがある、 *Visual Studio インストール パス*\Common7\IDE\ProjectTemplates と*Visual Studio インストール パス*\Common7\IDE\ItemTemplates ディレクトリ。 新しいプロジェクト ダイアログの最上位セクションの名前は完全に一致しないテンプレート フォルダーの名前。 これらが異なる場合は、テンプレート フォルダーの名前を使用します。  
  
     .Vsix ファイル拡張子、.zip を変更し、ファイルを開きます。  
  
2.  新しいプロジェクト ダイアログに、テンプレートが表示セクションと同じ名前で新しいフォルダーを作成します。  
  
3.  テンプレートのサブセクションに表示される場合、同じ名前のサブフォルダーを作成します。  
  
4.  テンプレートの .zip ファイルを新しいフォルダに移動します。  
  
5.  .Zip 拡張子を .vsix に変更します。  
  
6.  VSIX マニフェストを開きます。  
  
7.  VSIX マニフェストには、更新、**資産**ことは、テンプレート ファイルを格納するディレクトリ ツリーのルートを指すように、テンプレートのパス。 たとえば、テンプレートが \CSharp\Windows 内にある場合は、参照を指す必要があります \CSharp です。