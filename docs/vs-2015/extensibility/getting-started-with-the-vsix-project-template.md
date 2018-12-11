---
title: VSIX プロジェクト テンプレートの概要 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio SDK, VSIX project template
ms.assetid: 89fac33e-9380-4723-9b45-048a6e16f0ed
caps.latest.revision: 26
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1f7230bce49342ad8e31baeb3f46c72f1c45d776
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51787732"
---
# <a name="getting-started-with-the-vsix-project-template"></a>VSIX プロジェクト テンプレートの概要
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

拡張機能を作成するか、パッケージの展開の既存の拡張機能は、VSIX プロジェクト テンプレートを使用できます。 VSIX プロジェクト テンプレートは、Visual Basic と Visual c# の両方のバージョンを備え、Visual Studio SDK の一部としてインストールされます。  
  
 だけ、VSIX プロジェクト テンプレートを拡張機能に関する情報を含む source.extension.vsixmanifest ファイルと出荷の資産から成ります。  
  
 VSIX プロジェクト テンプレートを検索するには、Visual Studio SDK をインストールする必要があります。 詳細については、次を参照してください。 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)します。  
  
## <a name="deploying-a-custom-project-template-using-the-vsix-project-template"></a>VSIX プロジェクト テンプレートを使用してカスタム プロジェクト テンプレートをデプロイします。  
 次の手順では、VSIX プロジェクトを使用して、他の開発者と共有または Visual Studio ギャラリーにアップロードできるプロジェクト テンプレートをパッケージ化する方法を示します。  
  
1.  プロジェクト テンプレートを作成します。  
  
    1.  テンプレートを作成するためのプロジェクトを開きます。 このプロジェクトは、あらゆる種類のプロジェクトのできます。  
  
    2.  **[ファイル]** メニューの **[テンプレートのエクスポート]** をクリックします。 ウィザードの手順を実行します。  
  
         %USERPROFILE%\My documents \visual Studio で .zip ファイルが作成された*\<バージョン >* \My Exported Templates\\します。  
  
2.  空の VSIX プロジェクトを作成します。  
  
     **[ファイル]** メニューの **[新規作成]** をポイントし、 **[プロジェクト]** をクリックします。 いずれかを選択**Visual Basic**または**Visual c#** します。 選択したノードで、次のように選択します。**拡張**、し、 **VSIX プロジェクト**します。  
  
3.  .Zip ファイルをプロジェクトに追加します。 設定の**出力ディレクトリにコピー**プロパティを`Copy Always`します。  
  
4.  **ソリューション エクスプ ローラー**、ダブルクリックして、`source.extension.vsixmanifest`で開くファイルを**VSIX マニフェスト デザイナー**、し、次の変更。  
  
    -   設定、**製品名**フィールドを**マイ プロジェクト テンプレート**します。  
  
    -   設定、**製品 ID**フィールドを**MyProjectTemplate - 1**します。  
  
    -   設定、**作成者**フィールドを**Fabrikam**します。  
  
    -   設定、**説明**フィールドを**プロジェクト テンプレート**します。  
  
    -   **資産**セクションで、追加、 **Microsoft.VisualStudio.ProjectTemplate**を入力し、そのパスを .zip ファイルの名前に設定します。  
  
5.  保存して、source.extension.vsixmanifest ファイルを閉じます。  
  
6.  プロジェクトをビルドします。  
  
7.  出力ディレクトリには、.vsix ファイルをダブルクリックします。  
  
8.  A **VSIX インストーラー**メッセージ ボックスが表示されます。 拡張機能をインストールする手順に従います。  
  
9. Visual Studio を閉じて再度開きます。  
  
10. 選択**拡張機能と更新**(上、**ツール**メニュー) を選択し、**テンプレート**カテゴリ。 使用可能な拡張機能のいずれかにする必要があります**マイ プロジェクト テンプレート**します。  
  
11. 新しいプロジェクト テンプレートに表示される、**新しいプロジェクト**元のプロジェクト テンプレートと同じ場所にダイアログ。 たとえば、という名前のテンプレートを作成した**VB コンソール**から Visual Basic コンソール アプリケーションでは、 **VB コンソール**Visual Basic と同じペインが表示されます**のコンソールアプリケーション**テンプレート。  
  
#### <a name="to-specify-the-location-of-the-template-in-the-new-project-dialog-box"></a>新しいプロジェクト ダイアログ ボックスで、テンプレートの場所を指定するには  
  
1.  テンプレート フォルダーにある、 *Visual Studio インストール パス*\Common7\IDE\ProjectTemplates と*Visual Studio インストール パス*\Common7\IDE\ItemTemplates ディレクトリ。 新しいプロジェクト ダイアログの最上位レベルのセクションの名前のテンプレート フォルダーの名前が一致も一致しません。 これらが異なる場合は、テンプレート フォルダーの名前を使用します。  
  
     .Vsix ファイル拡張子を .zip に変更し、ファイルを開きます。  
  
2.  テンプレートが表示する必要があります、新しいプロジェクト ダイアログのセクションと同じ名前の新しいフォルダーを作成します。  
  
3.  テンプレートのサブセクションに表示される場合、同じ名前のサブフォルダーを作成します。  
  
4.  テンプレートの .zip ファイルを新しいフォルダに移動します。  
  
5.  .Zip 拡張子を .vsix に変更します。  
  
6.  VSIX マニフェストを開きます。  
  
7.  VSIX マニフェストでは、更新、**資産**ことは、テンプレート ファイルを格納するディレクトリ ツリーのルートを指すためのテンプレートのパス。 たとえば、\CSharp\Windows がテンプレートにある場合は、参照が \CSharp をポイントする必要があります。

