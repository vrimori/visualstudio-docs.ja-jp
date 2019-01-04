---
title: モジュールを使用して、ソリューションにファイルを含める |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deployment modules
- SharePoint development in Visual Studio, modules
- modules [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a9d8cf0da022c038c0e15e6b00f0bea0cdc3cef4
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53921550"
---
# <a name="use-modules-to-include-files-in-the-solution"></a>モジュールを使用して、ソリューションにファイルを含める
  新しいマスター ページなど、そのファイルの種類に関係なく、SharePoint サーバーにファイルをデプロイする場合がありますである可能性があります。 これを行うには、使用することができます*モジュール*(と混同しないように[!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]モジュールのコード)。 モジュールは、SharePoint ソリューション内のファイルのコンテナーです。 ソリューションを展開するときは、モジュール内のファイルが SharePoint サーバーの指定したフォルダーにコピーされます。  
  
## <a name="module-items-and-elements"></a>モジュールのアイテムと要素
 モジュールを作成するには、プロジェクトに追加でを選択して、**新しい項目の追加** ダイアログ ボックス。 次に、変更、 *Elements.xml*システムに配置されている場所とそのファイルが SharePoint サーバーにコピーする必要がありますが、配置するファイルの名前を含むファイル。  
  
 次の例に示します、 *Elements.xml*モジュール ファイル。  
  
```xml  
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
|*Elements.xml*|モジュールの定義ファイル。|  
|*Sample.txt*|モジュール内のファイルの例として機能するプレース ホルダー ファイル。|  
  
 *Elements.xml*ファイルには、次の要素が含まれています。  
  
|要素名|説明|  
|------------------|-----------------|  
|Elements|すべてのモジュールで定義されている要素が含まれます。|  
|Module|Module 要素が 1 つの属性を持つ*名前*の形式で、モジュールの名前を指定する`<Module Name="Module1">`します。<br /><br /> モジュールの名前を変更する場合 (またはその*フォルダー名*プロパティ)、Module 要素内の名前を手動で更新する必要があります。<br /><br /> モジュールの要素で、ファイルのサブディレクトリを指定する場合[!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)](WSS) がそれらの一致するディレクトリ構造を自動的に作成されます。|  
|ファイル|ファイルの要素が 2 つのパラメーター、*パス*と*Url*します。<br /><br /> パス:名前と、SharePoint ソリューション ファイルの場所。 形式は、`Path="Module1\Sample.txt"`します。<br /><br /> -Url:SharePoint サーバー上のファイルの配置場所です。 形式は、`Url="Module1/Sample.txt"`します。<br /><br /> 種類:2 つの設定を持つ省略可能な属性。*GhostableInLibrary*と*Ghostable*します。 形式は、`Type="GhostableInLibrary"`します。 指定する*GhostableInLibrary*ファイルはライブラリに追加されたときに、ファイルを伴う一覧項目と共に sharepoint ドキュメント ライブラリに追加することを意味します。 指定する*Ghostable*によりドキュメント ライブラリの外部の SharePoint に追加するファイル。|  
  
 展開する各ファイルには、個別が必要です。`<File>`要素エントリの*Elements.xml*します。  
  
## <a name="see-also"></a>関連項目
 [方法: モジュールを使用して、ファイルを含める](../sharepoint/how-to-include-files-by-using-a-module.md)   
 [操作方法：ファイルをプロビジョニングします。](http://go.microsoft.com/fwlink/?LinkID=144271)   
 [SharePoint ソリューションの開発](../sharepoint/developing-sharepoint-solutions.md)   
 [SharePoint の web パーツの作成](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [パッケージ化し、SharePoint ソリューションのデプロイ](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
