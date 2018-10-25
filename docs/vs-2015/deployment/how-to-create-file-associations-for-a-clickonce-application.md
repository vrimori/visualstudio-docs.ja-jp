---
title: '方法: ClickOnce アプリケーションのファイルの関連付けの作成 |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- file associations, ClickOnce applications
- ClickOnce deployment, file associations
ms.assetid: 835230c8-3177-440f-85e3-e40f1d8b4f9d
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: fd1bd7965f0277ce1d3d900be6ee10db097eeb3f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49909108"
---
# <a name="how-to-create-file-associations-for-a-clickonce-application"></a>方法 : ClickOnce アプリケーションのファイルの関連付けを作成する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] できるように、ユーザーがこれらの種類のファイルを開いたときに、アプリケーションを自動的に開始されます、アプリケーションが 1 つまたは複数のファイル名拡張子を関連付けることができます。 サポートするファイル名拡張子を[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]アプリケーションは簡単です。  
  
### <a name="to-create-file-associations-for-a-clickonce-application"></a>ClickOnce アプリケーションのファイルの関連付けを作成するには  
  
1. 作成、[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]アプリケーション通常は、使用して、既存または[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]アプリケーション。  
  
2. テキスト エディターまたはメモ帳などの XML エディターでは、アプリケーション マニフェストを開きます。  
  
3. `assembly` 要素を検索します。 詳細については、「[ClickOnce アプリケーション マニフェスト](../deployment/clickonce-application-manifest.md)」を参照してください。  
  
4. 子として、`assembly`要素を追加、`fileAssociation`要素。 `fileAssociation`要素には 4 つの属性。  
  
   - `extension`: アプリケーションに関連付けるファイル名拡張子。  
  
   - `description`: Windows シェルに表示されるファイルの種類の説明。  
  
   - `progid`: レジストリ内でマークする、ファイルの種類を一意に識別する文字列。  
  
   - `defaultIcon`: このファイルの種類を使用するアイコン。 アイコンは、アプリケーション マニフェストでファイルのリソースとして追加する必要があります。 詳細については、「 [方法 : ClickOnce アプリケーションにデータ ファイルを含める](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md)」を参照してください。  
  
     例については、`file`と`fileAssociation`、要素を参照してください[ \<fileAssociation > 要素](../deployment/fileassociation-element-clickonce-application.md)します。  
  
5. 1 つ以上のファイルの種類をアプリケーションに関連付ける場合は、さらに追加`fileAssociation`要素。 なお、`progid`属性ごとに異なる必要があります。  
  
6. アプリケーション マニフェストが完了したら、マニフェストに再署名します。 この設定は、Mage.exe を使用して、コマンドラインから行うことができます。  
  
    `mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx`  
  
    詳細については、次を参照してください[Mage.exe (マニフェスト生成および編集ツール)。](http://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)  
  
## <a name="see-also"></a>関連項目  
 [\<fileAssociation > 要素](../deployment/fileassociation-element-clickonce-application.md)   
 [ClickOnce アプリケーション マニフェスト](../deployment/clickonce-application-manifest.md)   
 [Mage.exe (マニフェストの生成および編集ツール)](http://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)



