---
title: '方法: ClickOnce アプリケーションのファイルの関連付けの作成 |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- file associations, ClickOnce applications
- ClickOnce deployment, file associations
ms.assetid: 835230c8-3177-440f-85e3-e40f1d8b4f9d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5f311705a6cb898ee9bff81a3bbad3890aea92c7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54947310"
---
# <a name="how-to-create-file-associations-for-a-clickonce-application"></a>方法: ClickOnce アプリケーションのファイルの関連付けを作成する
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] できるように、ユーザーがこれらの種類のファイルを開いたときに、アプリケーションを自動的に開始されます、アプリケーションが 1 つまたは複数のファイル名拡張子を関連付けることができます。 サポートするファイル名拡張子を[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーションは簡単です。  
  
### <a name="to-create-file-associations-for-a-clickonce-application"></a>ClickOnce アプリケーションのファイルの関連付けを作成するには  
  
1. 作成、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーション通常は、使用して、既存または[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーション。  
  
2. テキスト エディターまたはメモ帳などの XML エディターでは、アプリケーション マニフェストを開きます。  
  
3. `assembly` 要素を検索します。 詳細については、「[ClickOnce アプリケーション マニフェスト](../deployment/clickonce-application-manifest.md)」を参照してください。  
  
4. 子として、`assembly`要素を追加、`fileAssociation`要素。 `fileAssociation`要素には 4 つの属性。  
  
   - `extension`:アプリケーションに関連付けるファイル名拡張子。  
  
   - `description`:Windows シェルに表示されるファイルの種類の説明。  
  
   - `progid`:レジストリ内でマークする、ファイルの種類を一意に識別する文字列。  
  
   - `defaultIcon`:このファイルの種類を使用するアイコン。 アイコンは、アプリケーション マニフェストでファイルのリソースとして追加する必要があります。 詳細については、「[方法 :ClickOnce アプリケーションにデータ ファイルを含める](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md)」を参照してください。  
  
     例については、`file`と`fileAssociation`、要素を参照してください[ \<fileAssociation > 要素](../deployment/fileassociation-element-clickonce-application.md)します。  
  
5. 1 つ以上のファイルの種類をアプリケーションに関連付ける場合は、さらに追加`fileAssociation`要素。 なお、`progid`属性ごとに異なる必要があります。  
  
6. アプリケーション マニフェストが完了したら、マニフェストに再署名します。 使用して、コマンドラインから実行できる*Mage.exe*します。  
  
    `mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx`  
  
    詳しくは、「[Mage.exe (マニフェストの生成および編集ツール)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)」をご覧ください。  
  
## <a name="see-also"></a>関連項目  
 [\<fileAssociation > 要素](../deployment/fileassociation-element-clickonce-application.md)   
 [ClickOnce アプリケーション マニフェスト](../deployment/clickonce-application-manifest.md)   
 [Mage.exe (マニフェストの生成および編集ツール)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)