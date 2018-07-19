---
title: '方法: MSBuild タスクを使用した SharePoint ソリューション パッケージの作成 |Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5a95eb80b860a1447fe6e958edb9c98b66805a90
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/29/2018
ms.locfileid: "37119374"
---
# <a name="how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks"></a>方法: MSBuild タスクを使用した SharePoint ソリューション パッケージの作成
  ビルド、クリーンアップ、および SharePoint のパッケージを検証することができます (*.wsp*) MSBuild タスクのコマンドラインを使用して、開発用コンピューター。 ビルド コンピューターで Team Foundation Server を使用して、ビルド プロセスを自動化するのにこれらのコマンドを使用することもできます。  
  
## <a name="build-a-sharepoint-package"></a>SharePoint パッケージを作成します。  
  
#### <a name="to-build-a-sharepoint-package"></a>SharePoint パッケージを作成するには  
  
1.  Windows で**開始**] メニューの [選択**すべてのプログラム** > **アクセサリ** > **コマンド プロンプト**します。  
  
2.  SharePoint プロジェクトが配置されているディレクトリに変更します。  
  
3.  プロジェクトのパッケージを作成するには、次のコマンドを入力します。 置換*ProjectFileName*プロジェクトの名前に置き換えます。  
  
    ```cmd  
    msbuild /t:Package ProjectFileName  
    ```  
  
     たとえば、ListDefinition1 と呼ばれる SharePoint プロジェクトをパッケージ化するには、次のコマンドのいずれかを実行できます。  
  
    ```cmd  
    msbuild /t:Package ListDefinition1.vbproj  
    msbuild /t:Package ListDefinition1.csproj  
    ```  
  
## <a name="clean-a-sharepoint-package"></a>SharePoint パッケージをクリーンアップします。  
  
#### <a name="to-clean-a-sharepoint-package"></a>SharePoint パッケージをクリーンアップするには  
  
1.  コマンド プロンプト ウィンドウを開きます。  
  
2.  SharePoint プロジェクトが配置されているディレクトリに変更します。  
  
3.  プロジェクトのパッケージをクリーンアップするには、次のコマンドを入力します。 置換*ProjectFileName*プロジェクトの名前に置き換えます。  
  
    ```cmd  
    msbuild /t:CleanPackage ProjectFileName  
    ```  
  
     たとえば、ListDefinition1 と呼ばれる SharePoint プロジェクトをクリーンアップするには、次のコマンドのいずれかを実行できます。  
  
    ```cmd  
    msbuild /t:CleanPackage ListDefinition1.vbproj  
    msbuild /t:CleanPackage ListDefinition1.csproj  
    ```  
  
## <a name="validate-a-sharepoint-package"></a>SharePoint パッケージを検証します。  
  
#### <a name="to-validate-a-sharepoint-package"></a>SharePoint パッケージを検証するには  
  
1.  コマンド プロンプト ウィンドウを開きます。  
  
2.  SharePoint プロジェクトが配置されているディレクトリに変更します。  
  
3.  プロジェクトのパッケージを検証するには、次のコマンドを入力します。 置換*ProjectFileName*プロジェクトの名前に置き換えます。  
  
    ```cmd  
    msbuild /t:ValidatePackage ProjectFileName  
    ```  
  
     たとえば、ListDefinition1 と呼ばれる SharePoint プロジェクトを検証するには、次のコマンドのいずれかを実行できます。  
  
    ```cmd  
    msbuild /t:ValidatePackage ListDefinition1.vbproj  
    msbuild /t:ValidatePackage ListDefinition1.csproj  
    ```  
  
## <a name="set-properties-in-a-sharepoint-package"></a>SharePoint パッケージでプロパティを設定します。  
  
#### <a name="to-set-a-property-in-a-sharepoint-package"></a>SharePoint パッケージでプロパティを設定するには  
  
1.  コマンド プロンプト ウィンドウを開きます。  
  
2.  SharePoint プロジェクトが配置されているディレクトリに変更します。  
  
3.  プロジェクトのパッケージでプロパティを設定するには、次のコマンドを入力します。 置換*PropertyName*プロパティを設定するを使用します。  
  
    ```cmd  
    msbuild /property:PropertyName=Value  
    ```  
  
     たとえば、警告レベルを設定するには、次のコマンドを実行できます。  
  
    ```cmd  
    msbuild /property:WarningLevel = 2  
    ```  
  
## <a name="see-also"></a>関連項目
 [SharePoint の機能を作成します。](../sharepoint/creating-sharepoint-features.md)   
 [方法: SharePoint フィーチャーをカスタマイズ](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [方法: 項目を SharePoint の機能を追加および削除](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)  
