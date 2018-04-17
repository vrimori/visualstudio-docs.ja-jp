---
title: '方法: MSBuild タスクを使用して SharePoint ソリューション パッケージを作成 |Microsoft ドキュメント'
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
ms.openlocfilehash: 629b63b8645f1b5ebd84d25a04a4cec4e8bca6a3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks"></a>方法: MSBuild タスクを使用して SharePoint ソリューション パッケージを作成する
  ビルド、クリーンアップ、および、開発用コンピューターでコマンドラインの MSBuild タスクを使用して SharePoint パッケージ (.wsp) を検証することができます。 ビルド コンピューターに Team Foundation Server を使用して、ビルド プロセスを自動化するのにこれらのコマンドを使用することもできます。  
  
## <a name="building-a-sharepoint-package"></a>SharePoint パッケージの構築  
  
#### <a name="to-build-a-sharepoint-package"></a>SharePoint パッケージを作成するには  
  
1.  Windows の**開始**] メニューの [選択**すべてのプログラム**、**アクセサリ**、**コマンド プロンプト**です。  
  
2.  SharePoint プロジェクトが配置されているディレクトリを変更します。  
  
3.  プロジェクトのパッケージを作成するには、次のコマンドを入力します。 置き換える*ProjectFileName*プロジェクトの名前に置き換えます。  
  
    ```  
    msbuild /t:Package ProjectFileName  
    ```  
  
     たとえば、ListDefinition1 と呼ばれる SharePoint プロジェクトをパッケージ化するには、次のコマンドのいずれかを実行する可能性があります。  
  
    ```  
    msbuild /t:Package ListDefinition1.vbproj  
    msbuild /t:Package ListDefinition1.csproj  
    ```  
  
## <a name="cleaning-a-sharepoint-package"></a>SharePoint パッケージのクリーニング  
  
#### <a name="to-clean-a-sharepoint-package"></a>SharePoint パッケージをクリーンアップするのには  
  
1.  コマンド プロンプト ウィンドウを開きます。  
  
2.  SharePoint プロジェクトが配置されているディレクトリを変更します。  
  
3.  プロジェクトのパッケージをクリーンアップするのには、次のコマンドを入力します。 置き換える*ProjectFileName*プロジェクトの名前に置き換えます。  
  
    ```  
    msbuild /t:CleanPackage ProjectFileName  
    ```  
  
     たとえば、ListDefinition1 と呼ばれる SharePoint プロジェクトをクリーンアップするのには、次のコマンドのいずれかを実行する可能性があります。  
  
    ```  
    msbuild /t:CleanPackage ListDefinition1.vbproj  
    msbuild /t:CleanPackage ListDefinition1.csproj  
    ```  
  
## <a name="validating-a-sharepoint-package"></a>SharePoint パッケージの検証  
  
#### <a name="to-validate-a-sharepoint-package"></a>SharePoint パッケージを検証するには  
  
1.  コマンド プロンプト ウィンドウを開きます。  
  
2.  SharePoint プロジェクトが配置されているディレクトリを変更します。  
  
3.  プロジェクトのパッケージを検証するのには、次のコマンドを入力します。 置き換える*ProjectFileName*プロジェクトの名前に置き換えます。  
  
    ```  
    msbuild /t:ValidatePackage ProjectFileName  
    ```  
  
     たとえば、ListDefinition1 と呼ばれる SharePoint プロジェクトの検証には、次のコマンドのいずれかを実行する可能性があります。  
  
    ```  
    msbuild /t:ValidatePackage ListDefinition1.vbproj  
    msbuild /t:ValidatePackage ListDefinition1.csproj  
    ```  
  
## <a name="setting-properties-in-a-sharepoint-package"></a>SharePoint パッケージのプロパティの設定  
  
#### <a name="to-set-a-property-in-a-sharepoint-package"></a>SharePoint パッケージのプロパティを設定するには  
  
1.  コマンド プロンプト ウィンドウを開きます。  
  
2.  SharePoint プロジェクトが配置されているディレクトリを変更します。  
  
3.  プロジェクトのパッケージのプロパティを設定するには、次のコマンドを入力します。 置き換える*PropertyName*プロパティを設定するを使用します。  
  
    ```  
    msbuild /property:PropertyName=Value  
    ```  
  
     たとえば、警告レベルを設定するには、次のコマンドを実行する可能性があります。  
  
    ```  
    msbuild /property:WarningLevel = 2  
    ```  
  
## <a name="see-also"></a>関連項目  
 [SharePoint フィーチャーの作成](../sharepoint/creating-sharepoint-features.md)   
 [方法: SharePoint フィーチャーをカスタマイズ](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [方法: SharePoint フィーチャーの項目を追加および削除する](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)  
  
  