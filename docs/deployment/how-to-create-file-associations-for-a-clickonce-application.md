---
title: "方法: ClickOnce アプリケーションのファイルの関連付けを作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- file associations, ClickOnce applications
- ClickOnce deployment, file associations
ms.assetid: 835230c8-3177-440f-85e3-e40f1d8b4f9d
caps.latest.revision: "7"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 491de73e97bf44ea54d5ccdfb604924ff26c9530
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-create-file-associations-for-a-clickonce-application"></a>方法 : ClickOnce アプリケーションのファイルの関連付けを作成する
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーションでく 1 つまたは複数のファイル名拡張子に関連付けられているように、ユーザーの種類のファイルを開くときに、アプリケーションを自動的に開始されます。 ファイル名拡張子のサポートを追加する、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーションは簡単です。  
  
### <a name="to-create-file-associations-for-a-clickonce-application"></a>ClickOnce アプリケーションのファイルの関連付けを作成するには  
  
1.  作成、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーション通常は、既存の使用または[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーションです。  
  
2.  テキスト エディターまたはメモ帳などの XML エディターで、アプリケーション マニフェストを開きます。  
  
3.  `assembly` 要素を検索します。 詳細については、「[ClickOnce アプリケーション マニフェスト](../deployment/clickonce-application-manifest.md)」を参照してください。  
  
4.  子として、`assembly`要素を追加、`fileAssociation`要素。 `fileAssociation`要素には 4 つの属性。  
  
    -   `extension`: をアプリケーションに関連付けるファイル名拡張子。  
  
    -   `description`: Windows シェルに表示されるファイルの種類の説明。  
  
    -   `progid`: レジストリにマークする、ファイルの種類を一意に識別する文字列です。  
  
    -   `defaultIcon`: このファイルの種類を使用するアイコン。 アイコンは、アプリケーション マニフェストのファイル リソースとして追加する必要があります。 詳細については、「 [How to: Include a Data File in a ClickOnce Application](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md)」を参照してください。  
  
     例については、`file`と`fileAssociation`要素を参照してください[ \<fileAssociation > 要素](../deployment/fileassociation-element-clickonce-application.md)です。  
  
5.  1 つ以上のファイルの種類をアプリケーションに関連付ける場合は、追加`fileAssociation`要素。 なお、`progid`属性がごとに異なる必要があります。  
  
6.  アプリケーション マニフェストを伴うが終了したら、マニフェストに再署名します。 この設定は、Mage.exe を使用してコマンドラインから行うことができます。  
  
     `mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx`  
  
     詳細については、次を参照してください[Mage.exe (マニフェスト生成および編集ツール)。](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)  
  
## <a name="see-also"></a>関連項目  
 [\<fileAssociation > 要素](../deployment/fileassociation-element-clickonce-application.md)   
 [ClickOnce アプリケーション マニフェスト](../deployment/clickonce-application-manifest.md)   
 [Mage.exe (マニフェストの生成および編集ツール)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)