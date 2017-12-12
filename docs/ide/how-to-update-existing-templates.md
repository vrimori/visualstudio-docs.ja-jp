---
title: "方法 : 既存のテンプレートを更新する | Microsoft Docs"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- item templates, updating existing templates
- Visual Studio templates, updating existing templates
- project templates, updating existing templates
ms.assetid: d585e45b-7fe2-45fa-9cf3-7f2bc060f3c4
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0fffcc55953e394c5efd00b86949f04474a66111
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-update-existing-templates"></a>方法 : 既存のテンプレートを更新する
テンプレートを作成し、複数のファイルを .zip ファイルに圧縮した後で、テンプレートを変更できます。 それには、テンプレートのファイルを手動で変更するか、テンプレートに基づいてプロジェクトから新しいテンプレートをエクスポートします。  
  
## <a name="using-the-export-template-wizard-to-update-an-existing-template"></a>テンプレートのエクスポート ウィザードの使用による既存のテンプレートの更新  
Visual Studio には**テンプレートのエクスポート** ウィザードが用意されており、これを使用して既存のテンプレートを更新することができます。  
  
#### <a name="to-use-export-template-to-update-an-existing-template"></a>テンプレートのエクスポートを使用して既存のテンプレートを更新するには  
  
1.  **[ファイル]**、**[新規]**、**[プロジェクト]** の順に選択して、**[新しいプロジェクト]** ダイアログ ボックスを開きます。  
  
2.  更新するテンプレートを選択し、プロジェクトの名前と場所を入力して、**[OK]** を選択します。  
  
3.  Visual Studio でプロジェクトを変更します。  
  
4.  **[プロジェクト]** メニューの **[テンプレートのエクスポート]** を選択します。  

    **テンプレートのエクスポート ウィザード**が開きます。  

5.  ウィザードの指示に従って、テンプレートを .zip ファイルとしてエクスポートします。  

6.  古いテンプレートの .zip ファイルを削除します。  
  
## <a name="manually-updating-an-existing-template"></a>既存のテンプレートの手動での更新  
Visual Studio の外部で既存のテンプレートを更新するには、圧縮された .zip ファイル内のファイルを変更します。  
  
#### <a name="to-manually-update-an-existing-template"></a>既存のテンプレートを手動で更新するには  
  
1.  テンプレートを含む .zip ファイルを探します。 既定では、このファイルは %USERPROFILE%\Documents\Visual Studio \<バージョン\>\My Exported Templates\. にあります。  
  
2.  .zip ファイルを展開します。  
  
3.  現在のテンプレート ファイルを変更または削除するか、テンプレートに新しいファイルを追加します。  
  
4.  .vstemplate XML ファイルを開いたり、変更したり、保存したりして、更新された動作または新しいファイルを処理します。  

    .vstemplate スキーマの詳細については、「[Visual Studio テンプレートのスキーマ参照](../extensibility/visual-studio-template-schema-reference.md)」を参照してください。 ソース ファイルでパラメーター化できる内容の詳細については、「[テンプレート パラメーター](../ide/template-parameters.md)」を参照してください。  
  
5.  テンプレート内のファイルを選択して右クリックし、**[送る]** を選択してから **[圧縮 (zip 形式) フォルダー]** を選択します。  

    選択したファイルは .zip ファイルに圧縮されます。  
  
6.  新しい .zip ファイルを古い .zip ファイルと同じディレクトリに配置します。  
  
7.  抽出したテンプレート ファイルと古いテンプレート .zip ファイルを削除します。  
  
8.  次のようにして、開発者コマンド プロンプトの昇格されたインスタンスを開始します。  

  1. [スタート] メニューで、**[Visual Studio \<バージョン\>]**、**[開発者コマンド プロンプト]** の順に移動します。  

  2. コンテキスト (右クリック) メニューから、**[その他]**、**[管理者として実行]** の順に選択します。  
  
9. 次のコマンドを実行します: `devenv /installvstemplates`  
  
## <a name="see-also"></a>関連項目  
[テンプレートのカスタマイズ](../ide/customizing-project-and-item-templates.md)   
[プロジェクトと項目テンプレートの作成](../ide/creating-project-and-item-templates.md)   
[Visual Studio テンプレート スキーマ参照](../extensibility/visual-studio-template-schema-reference.md)   
[テンプレート パラメーター](../ide/template-parameters.md)   
[方法 : スタート キットを作成する](../ide/how-to-create-starter-kits.md)