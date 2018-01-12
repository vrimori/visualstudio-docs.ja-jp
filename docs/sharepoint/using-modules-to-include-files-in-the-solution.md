---
title: "モジュールを使用して、ソリューション内のファイルのインクルード |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deployment modules
- SharePoint development in Visual Studio, modules
- modules [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: c7f0fff081215e1bf1a9e2c5320668f2c698b2e6
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="using-modules-to-include-files-in-the-solution"></a>モジュールを使用してソリューションにファイルを追加する
  新しいマスター ページなど、そのファイルの種類に関係なく、SharePoint サーバーにファイルを配置する場合がありますである可能性があります。 これを行うには、使用することができます*モジュール*(と混同しないでください[!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]モジュールのコード)。 モジュールは、SharePoint ソリューションのファイルのコンテナーです。 ソリューションを配置するときに、モジュール内のファイルは、SharePoint サーバーで、指定したフォルダーにコピーされます。  
  
## <a name="module-items-and-elements"></a>モジュールの項目と要素  
 モジュールを作成するプロジェクトを選択して、追加で、**新しい項目の追加** ダイアログ ボックス。 次に、展開、システムに配置されているし、SharePoint サーバーにコピーするファイルの名前を含めるには、その Elements.xml ファイルを変更します。  
  
 モジュールの Elements.xml ファイルの例を次に示します。  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
    <Module Name="Module1">  
        <File Path="Module1\Sample.txt" Url="Module1/Sample.txt" />  
    </Module>  
</Elements>  
  
```  
  
 新しく作成されたモジュールには、次の既定のファイルが含まれます。  
  
|ファイル名|説明|  
|---------------|-----------------|  
|Elements.xml|モジュールの定義ファイル。|  
|Sample.txt|モジュール内のファイルの例として機能するプレース ホルダー ファイル。|  
  
 Elements.xml ファイルには、次の要素が含まれています。  
  
|要素名|説明|  
|------------------|-----------------|  
|Elements|すべてのモジュールで定義されている要素が含まれています。|  
|Module|Module 要素が 1 つの属性を持つ*名前*の形式で、モジュールの名前を指定する`<Module Name="Module1">`です。<br /><br /> モジュールの名前を変更する場合 (またはその*フォルダー名*プロパティ)、モジュールの要素の名前を手動で更新する必要があります。<br /><br /> Module 要素で、ファイルのサブディレクトリを指定する場合[!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)](WSS) がそれらの一致するディレクトリ構造を自動的に作成されます。|  
|ファイル|ファイルの要素が 2 つのパラメーターを持つ*パス*と*Url*です。<br /><br /> パス: 名前と、SharePoint ソリューション内のファイルの場所。 形式は、`Path="Module1\Sample.txt"`です。<br /><br /> -Url: SharePoint サーバー上のファイルの展開先の場所です。 形式は、`Url="Module1/Sample.txt"`です。<br /><br /> 型: 省略可能な属性を持つ 2 つの設定: *GhostableInLibrary*と*Ghostable*です。 形式は、`Type="GhostableInLibrary"`です。 指定する*GhostableInLibrary*ファイルはライブラリに追加されたときに、ファイルに付随するリスト アイテムと共に sharepoint ドキュメント ライブラリに追加することを意味します。 指定する*Ghostable*ドキュメント ライブラリの外側を SharePoint に追加するファイルが実行されます。|  
  
 展開する各ファイルが個別の必要があります`<File>`Elements.xml 内の要素のエントリ。  
  
## <a name="see-also"></a>参照  
 [方法: モジュールを使用して、ファイルを含める](../sharepoint/how-to-include-files-by-using-a-module.md)   
 [方法: ファイルを準備](http://go.microsoft.com/fwlink/?LinkID=144271)   
 [SharePoint ソリューションの開発](../sharepoint/developing-sharepoint-solutions.md)   
 [SharePoint の Web パーツの作成](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [SharePoint ソリューションのパッケージ化と配置](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  