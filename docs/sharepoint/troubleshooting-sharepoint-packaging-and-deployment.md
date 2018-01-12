---
title: "SharePoint のパッケージ化と配置のトラブルシューティング |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/22/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VSTO.WorkflowDeployment.Troubleshooting
- VS.SharePointTools.Project.PackageRetraction
- VS.SharePointTools.Deployment.Troubleshooting
- VS.SharePointTools.Deploying.Troubleshooting
- VS.SharePointTools.Project.DeploymentTroubleshooting
- VS.SharePointTools.Project.SharePointNotInstalled
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packaging
- SharePoint development in Visual Studio, troubleshooting
- SharePoint development in Visual Studio, deployment conflict resolution
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: a2c9cbb7b0b9e7f0536fb393bcea3d0873e0d90a
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="troubleshooting-sharepoint-packaging-and-deployment"></a>SharePoint のパッケージ化と配置のトラブルシューティング
  このトピックでは、SharePoint ソリューションをパッケージ化および配置するときに発生する可能性があるさまざまな問題について説明します。  
  
## <a name="enabling-enhanced-debugging"></a>拡張デバッグの有効化  
 Visual Studio、SharePoint、およびその他のレイヤーの間で問題を診断する場合は、EnableDiagnostics レジストリ キーを使用してスタック トレースを表示することができます。 詳細については、次を参照してください。 [SharePoint ソリューションのデバッグ](../sharepoint/debugging-sharepoint-solutions.md)です。  
  
## <a name="adding-project-output-to-the-solution-package"></a>ソリューション パッケージへのプロジェクト出力の追加  
 パッケージ デザイナーを使用してパッケージにプロジェクト出力を追加することができます。 ただし、プロジェクト出力を追加する際には、そのプロジェクトのプラットフォームが SharePoint ソリューションのプラットフォームと一致していることを確認する必要があります。 使用することをお勧め、 **Any CPU** SharePoint サーバーに配置するアセンブリのプラットフォーム ターゲットです。 詳細については、次を参照してください。 [[コンパイル] ページ、プロジェクト デザイナー &#40;です。Visual Basic &#41;](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)と[コンパイラ設定 ダイアログ ボックス &#40; を高度なVisual Basic &#41;](/visualstudio/ide/reference/advanced-compiler-settings-dialog-box-visual-basic).  
  
## <a name="validation-warnings-and-errors"></a>検証の警告とエラー  
 Visual Studio の SharePoint 開発ツールでは、ソリューション パッケージが正しい形式になっていることを確認するために検証ステップが実行されます。 特定のフィーチャーやパッケージのためのカスタム検証ステップを作成することもできます。 詳細については、次を参照してください。[する方法: カスタム機能の作成と SharePoint ソリューションのパッケージ検証規則](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md)です。  
  
## <a name="deployment-conflict-resolution"></a>配置競合の解決  
 SharePoint ソリューションを配置する際に、ソリューション パッケージ内の項目と同じ名前、URL、または ID を持つ項目がサーバー上にあると、競合が発生します。 変更することができます、**配置競合の解決**プロパティを解決するには、レポート、またはモジュール、Web パーツ、リスト インスタンス、およびコンテンツの種類の競合を無視します。  
  
 設定を次の表に示します、**配置競合の解決**プロパティです。  
  
|[値]|説明|  
|-----------|-----------------|  
|自動|競合を検出して自動的に解決します。|  
|プロンプト|競合を検出し、解決する前に開発者に報告します。|  
|なし|競合を検出しません。|  
  
## <a name="differences-between-f5-deployment"></a>F5 キーによる配置の違い  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] を使用してテストおよびデバッグのために SharePoint プロジェクトをローカル SharePoint サーバーに配置する際に、いくつかの追加の手順が [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] によって実行されます。  
  
1.  配置手順の間にインターネット インフォメーション サービス (IIS) がリセットされます。  
  
2.  ワークフローが自動的に関連付けられます。  
  
3.  パッケージ デザイナーの階層構造に従ってフィーチャーのアクティブ化の順序が設定されます。  
  
 カスタムの配置手順を追加して F5 キーの動作をさらに変更することもできます。 詳細については、次を参照してください。[チュートリアル: SharePoint プロジェクトのカスタム配置手順の作成](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)です。  
  
## <a name="delay-displaying-sharepoint-page-when-deploying-visual-web-part"></a>可視 Web パーツを配置するときの SharePoint ページの表示の遅延  
 [!INCLUDE[wiprlhext](../sharepoint/includes/wiprlhext-md.md)]、[!INCLUDE[win7](../sharepoint/includes/win7-md.md)]、または [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] の Bin フォルダーに可視 Web パーツを配置するときに、SharePoint ページの表示に時間がかかります。 これは、Bin ディレクトリなどの最上位の [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] ディレクトリのファイルを変更すると Web アプリケーション全体が再コンパイルされるためです。 結果として、SharePoint ページの表示に最大で 25 秒の遅延が生じます。  
  
### <a name="error-message"></a>エラー メッセージ  
 なし。  
  
### <a name="resolution"></a>解像度  
 この問題を回避するには、次の手順を実行します。  
  
1.  マイクロソフト サポートの記事で説明したように、KB967535 更新プログラムをインストール[修正: 修正プログラムを Windows Vista および Windows Server 2008 の IIS 7.0 で ASP.NET で 2 つの問題を修正する](http://go.microsoft.com/fwlink/?LinkId=179055)です。  
  
2.  次の行を Web.config ファイルに追加します。  
  
    ```  
    <compilation batch="false" optimizeCompilations="true">  
    ```  
  
## <a name="sharepoint-project-deployment-fails-with-error-failed-to-extract-the-cab-file-in-the-solution"></a>SharePoint プロジェクトの配置が "ソリューションで cab ファイルを抽出できませんでした" というエラーで失敗する  
 いずれかの SharePoint プロジェクト項目の名前にかっこが含まれると、そのソリューションの配置は次のエラーで失敗します。  
  
### <a name="error-message"></a>エラー メッセージ  
 配置手順 'ソリューションの追加' でエラーが発生しました: ソリューションで cab ファイルを抽出できませんでした  
  
### <a name="resolution"></a>解像度  
 この問題を回避するには、SharePoint プロジェクト項目の名前に含まれるかっこを削除してください。  
  
## <a name="error-appears-when-deploying-a-visual-web-part-to-a-site-on-a-different-web-application"></a>別の Web アプリケーションのサイトに可視 Web パーツを配置するとエラーが表示される  
 可視 Web パーツの SiteUrl プロパティを変更することで、Web アプリケーション上のサイトに現在配置されているものとは異なる可視 Web パーツを初めて配置するときに、エラーが発生します。  
  
### <a name="error-message"></a>エラー メッセージ  
 配置手順 'ソリューションの追加' でエラーが発生しました: ID [#] の機能は既にこのファームにインストールされています。 機能を明示的に再インストールするには、force 属性を使用してください。  
  
### <a name="resolution"></a>解像度  
 このエラーは、可視 Web パーツ フィーチャーが SharePoint で取り消される方法によって発生します。 可視 Web パーツを正常に配置するには、F5 キーを押して再度ソリューションを配置してください。  
  
## <a name="warning-appears-when-deploying-nested-user-controls"></a>入れ子になったユーザー コントロールを配置すると警告が表示される  
 この警告は、ユーザー コントロールを含む可視 Web パーツや、可視 Web パーツや別のユーザー コントロールを含むユーザー コントロールなどの、入れ子になったユーザー コントロールが存在する SharePoint ソリューションを配置したときに発生します。 この警告は、ツールボックスからドラッグするかを使用して、デザイナーにコントロールを追加するかどうかが発生した、@Registerソース ビューのディレクティブ。  
  
### <a name="error-message"></a>エラー メッセージ  
 警告 1 要素 ' [*コントロール名*]' は既知の要素ではありません。 Web サイトにコンパイル エラーがあるか、web.config ファイルが存在しない可能性があります。  
  
### <a name="resolution"></a>解像度  
 場合、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]プロジェクト システムは、入れ子になったユーザー コントロールを認識することはありません、Intellisense を提供できないし、警告を出力します。 プロジェクト システムで入れ子になったユーザー コントロールの認識されない、プロジェクトがビルドされず、デザイナーが閉じられていないと、再び開かれます場合や、自動取り消しオプションが有効になっている、それが原因で、ユーザー コントロールをデバッグ後に SharePoint ハイブから取り消します。  
  
 この警告を除去するには、プロジェクトをビルドしてからデザイナーを閉じて再度開くか、プロジェクトに対する自動取り消しオプションを無効にします。 これを行うには、クリア、**デバッグ後に自動取り消し**チェック ボックスをオン、 **SharePoint**プロジェクトのプロパティ ダイアログ ボックスのタブです。  
  
## <a name="see-also"></a>参照  
 [SharePoint ソリューションのパッケージ化と配置](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  
