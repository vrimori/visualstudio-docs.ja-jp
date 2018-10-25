---
title: '方法 : テンプレートの問題を解決する | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio templates, troubleshooting
ms.assetid: 3e577ad2-f725-4c11-93b3-477f2404ec81
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a68097745de1f1d94e5c09963a474a0095588fba
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49296427"
---
# <a name="how-to-troubleshoot-templates"></a>方法 : テンプレートの問題を解決する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

テンプレートを開発環境に読み込むことができない場合に、問題を突き止める方法はいくつかあります。  
  
## <a name="validating-the-vstemplate-file"></a>.vstemplate ファイルの検証  
 テンプレートの .vstemplate ファイルが [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] テンプレート スキーマに準拠していないと、テンプレートが **[新しいプロジェクト]** ダイアログ ボックスに表示されないことがあります。  
  
#### <a name="to-validate-the-vstemplate-file"></a>.vstemplate ファイルを検証するには  
  
1.  テンプレートを含む .zip ファイルを探します。  
  
2.  .zip ファイルを展開します。  
  
3.  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] の **[ファイル]** メニューの **[開く]** をクリックし、**[ファイル]** をクリックします。  
  
4.  テンプレートの .vstemplate ファイルを選択し、**[開く]** をクリックします。  
  
5.  .vstemplate ファイルの XML が [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] テンプレート スキーマに準拠していることを確認します。 .vstemplate スキーマの詳細については、「[Visual Studio テンプレート スキーマ参照](../extensibility/visual-studio-template-schema-reference.md)」を参照してください。  
  
    > [!NOTE]
    >  .Vstemplate ファイルを作成する際に IntelliSense サポートを取得するには追加、`xmlns`属性を`VSTemplate`要素の値を割り当てると http://schemas.microsoft.com/developer/vstemplate/2005します。  
  
6.  .vstemplate ファイルを保存して、閉じます。  
  
7.  テンプレートに含まれるファイルを選択して右クリックし、**[送る]** を選択し、**[圧縮 (zip 形式) フォルダー]** をクリックします。 選択したファイルは .zip ファイルに圧縮されます。  
  
8.  新しい .zip ファイルを古い .zip ファイルと同じディレクトリに配置します。  
  
9. 抽出したテンプレート ファイルと古いテンプレート .zip ファイルを削除します。  
  
## <a name="monitoring-the-event-log"></a>イベント ログの監視  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] は、テンプレート .zip ファイルの処理中に発生したエラーを記録します。 **[新しいプロジェクト]** ダイアログ ボックスに表示されるはずのテンプレートが表示されない場合は、**[イベント ビューアー]** を使用して問題のトラブルシューティングを行うことができます。  
  
#### <a name="to-locate-template-errors-in-event-viewer"></a>イベント ビューアーでテンプレート エラーを見つけるには  
  
1.  Windows で、**[スタート]** をクリックし、**[コントロール パネル]** をクリックします。次に、**[管理ツール]** をダブルクリックし、**[イベント ビューアー]** をダブルクリックします。  
  
2.  左ウィンドウで、**[アプリケーション]** をクリックします。  
  
3.  **[ソース]** の値が [`Visual Studio - VsTemplate`] のイベントを探します。  
  
4.  テンプレート イベントをダブルクリックして、エラーを表示します。  
  
## <a name="see-also"></a>関連項目  
 [テンプレートのカスタマイズ](../ide/customizing-project-and-item-templates.md)   
 [プロジェクトと項目テンプレートの作成](../ide/creating-project-and-item-templates.md)   
 [Visual Studio テンプレート スキーマ参照](../extensibility/visual-studio-template-schema-reference.md)



