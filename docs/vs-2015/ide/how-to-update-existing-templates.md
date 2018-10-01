---
title: '方法: 既存のテンプレートの更新 |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- item templates, updating existing templates
- Visual Studio templates, updating existing templates
- project templates, updating existing templates
ms.assetid: d585e45b-7fe2-45fa-9cf3-7f2bc060f3c4
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9c5d091e58904cae058c5a2a5ade1b8ceec4c738
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47536794"
---
# <a name="how-to-update-existing-templates"></a>方法 : 既存のテンプレートを更新する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[方法: 既存のテンプレートを更新](https://docs.microsoft.com/visualstudio/ide/how-to-update-existing-templates)します。  
  
テンプレートを作成し、複数のファイルを .zip ファイルに圧縮した後で、テンプレートを変更できます。 それには、テンプレートのファイルを手動で変更するか、テンプレートに基づいてプロジェクトから新しいテンプレートをエクスポートします。  
  
## <a name="using-the-export-template-wizard-to-update-an-existing-template"></a>テンプレートのエクスポート ウィザードの使用による既存のテンプレートの更新  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 提供、**テンプレートのエクスポート**ウィザード、既存のテンプレートを更新するために使用できます。  
  
#### <a name="to-use-export-template-to-update-an-existing-template"></a>テンプレートのエクスポートを使用して既存のテンプレートを更新するには  
  
1.  **[ファイル]** メニューの **[新規作成]** をポイントし、 **[新しいプロジェクト]** をクリックします。  
  
2.  更新、名前と、一時プロジェクトの場所を入力します をクリックしたいテンプレートを選択して**OK**します。  
  
3.  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] でプロジェクトを変更します。  
  
4.  **ファイル** メニューのをクリックして**テンプレートのエクスポート**を使用して、**テンプレートのエクスポート**新しいテンプレートを作成するウィザード。  
  
5.  更新されたテンプレートが .zip ファイルに圧縮されたら、古いテンプレートの .zip ファイルを削除します。  
  
## <a name="manually-updating-an-existing-template"></a>既存のテンプレートの手動での更新  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] の外部で既存のテンプレートを更新するには、圧縮された .zip ファイル内のファイルを変更します。  
  
#### <a name="to-manually-update-an-existing-template"></a>既存のテンプレートを手動で更新するには  
  
1.  テンプレートを含む .zip ファイルを探します。 既定では、このファイルにある \My Documents\Visual Studio*バージョン*\My Exported Templates\\します。  
  
2.  .zip ファイルを展開します。  
  
3.  現在のテンプレート ファイルを変更または削除するか、テンプレートに新しいファイルを追加します。  
  
4.  .vstemplate XML ファイルを開いたり、変更したり、保存したりして、更新された動作または新しいファイルを処理します。 .vstemplate スキーマの詳細については、「[Visual Studio テンプレートのスキーマ参照](../extensibility/visual-studio-template-schema-reference.md)」を参照してください。 ソース ファイルでパラメーター化できる内容の詳細については、次を参照してください[テンプレート パラメーター。](../ide/template-parameters.md)  
  
5.  テンプレートで、ファイルを右クリックし、をクリック選択します。**送信**、順にクリックします**圧縮 (zip 形式) フォルダー**します。 選択したファイルは .zip ファイルに圧縮されます。  
  
6.  新しい .zip ファイルを古い .zip ファイルと同じディレクトリに配置します。  
  
7.  抽出したテンプレート ファイルと古いテンプレート .zip ファイルを削除します。  
  
8.  (管理者) としてインスタンスの開発者コマンド プロンプトを起動します。 (スタート メニューで、 **Visual Studio 2010/Visual Studio ツール/開発者コマンド プロンプト**)。  
  
9. 次のコマンドを実行します: `devenv /installvstemplates`  
  
## <a name="see-also"></a>関連項目  
 [テンプレートのカスタマイズ](../ide/customizing-project-and-item-templates.md)   
 [プロジェクトと項目テンプレートの作成](../ide/creating-project-and-item-templates.md)   
 [Visual Studio テンプレート スキーマ参照](../extensibility/visual-studio-template-schema-reference.md)   
 [テンプレート パラメーター](../ide/template-parameters.md)   
 [方法 : スタート キットを作成する](../ide/how-to-create-starter-kits.md)



