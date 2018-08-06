---
title: VSIX プロジェクト テンプレートの概要 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, VSIX project template
ms.assetid: 89fac33e-9380-4723-9b45-048a6e16f0ed
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 28aa6c6e2b7aca671b1f1ac9d9be7f34261b867b
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/03/2018
ms.locfileid: "39499440"
---
# <a name="get-started-with-the-vsix-project-template"></a>VSIX プロジェクト テンプレートを概要します。
拡張機能を作成するか、パッケージの展開の既存の拡張機能は、VSIX プロジェクト テンプレートを使用できます。 VSIX プロジェクト テンプレートは、Visual Basic と Visual c# の両方のバージョンを備え、Visual Studio SDK の一部としてインストールされます。  
  
 VSIX プロジェクト テンプレートは構成だけを*source.extension.vsixmanifest*ファイルで、出荷、拡張機能と、資産に関する情報が含まれます。  
  
 VSIX プロジェクト テンプレートを検索するには、Visual Studio SDK をインストールする必要があります。 詳細については、次を参照してください。 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)します。  
  
## <a name="deploy-a-custom-project-template-using-the-vsix-project-template"></a>VSIX プロジェクト テンプレートを使用してカスタム プロジェクト テンプレートのデプロイします。  
 次の手順では、VSIX プロジェクトを使用して、他の開発者と共有または Visual Studio ギャラリーにアップロードできるプロジェクト テンプレートをパッケージ化する方法を示します。  
  
1.  プロジェクト テンプレートを作成します。  
  
    1.  テンプレートを作成するためのプロジェクトを開きます。 このプロジェクトは、あらゆる種類のプロジェクトのできます。  
  
    2.  **[プロジェクト]** メニューの **[テンプレートのエクスポート]** をクリックします。 ウィザードの手順を実行します。  
  
         A *.zip*にファイルが作成 *%USERPROFILE%\My documents \visual Studio\<バージョン > \My Exported Templates\\*します。  
  
2.  空の VSIX プロジェクトを作成します。  
  
     **[ファイル]** メニューの **[新規作成]** をポイントし、 **[プロジェクト]** をクリックします。 いずれかを選択**Visual Basic**または**Visual c#** します。 選択したノードで、次のように選択します。**拡張**、し、 **VSIX プロジェクト**します。  
  
3.  追加、 *.zip*ファイルをプロジェクトにします。 設定の**出力ディレクトリにコピー**プロパティを`Copy Always`します。  
  
4.  **ソリューション エクスプ ローラー**、ダブルクリックして、 *source.extension.vsixmanifest*で開くファイルを**VSIX マニフェスト デザイナー**、し、次の変更。  
  
    -   設定、**製品名**フィールドを**マイ プロジェクト テンプレート**します。  
  
    -   設定、**製品 ID**フィールドを**MyProjectTemplate - 1**します。  
  
    -   設定、**作成者**フィールドを**Fabrikam**します。  
  
    -   設定、**説明**フィールドを**プロジェクト テンプレート**します。  
  
    -   **資産**セクションで、追加、 **Microsoft.VisualStudio.ProjectTemplate**を入力し、そのパスの名前に設定、 *.zip*ファイル。  
  
5.  保存して閉じます、 *source.extension.vsixmanifest*ファイル。  
  
6.  プロジェクトをビルドします。  
  
7.  出力ディレクトリをダブルクリック、 *.vsix*ファイル。  
  
8.  A **VSIX インストーラー**メッセージ ボックスが表示されます。 拡張機能をインストールする手順に従います。  
  
9. Visual Studio を閉じて再度開きます。  
  
10. 選択**拡張機能と更新**(上、**ツール**メニュー) を選択し、**テンプレート**カテゴリ。 使用可能な拡張機能のいずれかにする必要があります**マイ プロジェクト テンプレート**します。  
  
11. 新しいプロジェクト テンプレートに表示される、**新しいプロジェクト**元のプロジェクト テンプレートと同じ場所にダイアログ。 たとえば、という名前のテンプレートを作成した**VB コンソール**から Visual Basic コンソール アプリケーションでは、 **VB コンソール**Visual Basic と同じペインが表示されます**のコンソールアプリケーション**テンプレート。  
  
### <a name="to-specify-the-location-of-the-template-in-the-new-project-dialog-box"></a>新しいプロジェクト ダイアログ ボックスで、テンプレートの場所を指定するには  
  
1.  テンプレート フォルダーにある、 *{Visual Studio インストール パス} \Common7\IDE\ProjectTemplates*と * {Visual Studio インストール パス} \Common7\IDE\ItemTemplates} ディレクトリ。 上部の名前のレベルのセクションで、**新しいプロジェクト**ダイアログは、テンプレート フォルダーの名前と一致しません。 これらが異なる場合は、テンプレート フォルダーの名前を使用します。  
  
     変更、 *.vsix*ファイルに拡張子 *.zip*、し、ファイルを開きます。  
  
2.  セクションと同じ名前の新しいフォルダーを作成、**新しいプロジェクト**ダイアログにテンプレートが表示する必要があります。  
  
3.  テンプレートのサブセクションに表示される場合、同じ名前のサブフォルダーを作成します。  
  
4.  テンプレートを移動 *.zip*新しいフォルダにファイル。  
  
5.  変更、 *.zip*拡張機能を *.vsix*します。  
  
6.  VSIX マニフェストを開きます。  
  
7.  VSIX マニフェストでは、更新、**資産**ことは、テンプレート ファイルを格納するディレクトリ ツリーのルートを指すためのテンプレートのパス。 たとえば、次のテンプレートが*\CSharp\Windows*、参照が指す必要があります*\CSharp*します。