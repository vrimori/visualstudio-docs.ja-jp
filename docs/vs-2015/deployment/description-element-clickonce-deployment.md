---
title: '&lt;説明&gt;要素 (ClickOnce 配置) |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#description
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <description> element [ClickOnce deployment manifest]
ms.assetid: 18f6919e-a3ab-4942-a57d-167fabfac44e
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 8ddba6356ab051dbad27e55eefd53a517b47a21a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49224771"
---
# <a name="ltdescriptiongt-element-clickonce-deployment"></a>&lt;説明&gt;要素 (ClickOnce 配置)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

シェル プレゼンスの作成とコントロール パネルの**プログラム追加と削除**の項目に使用されるアプリケーション情報を識別します。  
  
## <a name="syntax"></a>構文  
  
```  
  
      <description   
   publisher   
   product  
   suiteName  
   supportUrl  
/>  
```  
  
## <a name="elements-and-attributes"></a>要素と属性  
 `description` 要素は必須です。この要素は `urn:schemas-microsoft-com:asm.v1` 名前空間に属します。 これは、子要素を含まず、かつ、次の属性を持ちます。   
  
|属性|説明|  
|---------------|-----------------|  
|`publisher`|必須。 Windows でアイコンの配置に使用する会社名を識別する**開始**メニューおよび**プログラム追加と削除**インストールの展開が構成されている場合、コントロール パネルの。|  
|`product`|必須。 完全な製品名を識別します。 Windows にインストールされているアイコンのタイトルとして使用される**開始**メニュー。|  
|`suiteName`|任意。 内のサブフォルダーを識別、`publisher`フォルダー、Windows で**開始**メニュー。|  
|`supportUrl`|任意。 表示されるサポート URL を指定します、**プログラム追加と削除**コントロール パネルの項目。 この URL へのショートカットは、Windows でのアプリケーションのサポートの作成も**開始**] メニューの [インストールの展開が構成されている場合。|  
  
## <a name="remarks"></a>Remarks  
 Description 要素は、すべての展開構成に必要です。  
  
## <a name="example"></a>例  
 次のコード例を示しています、`description`内の要素を[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]配置マニフェスト。 このコード例が示されている例の一部、 [ClickOnce 配置マニフェスト](../deployment/clickonce-deployment-manifest.md)トピック。  
  
```  
<description   
  asmv2:publisher="My Company Name"  
  asmv2:product="My Application"  
  xmlns="urn:schemas-microsoft-com:asm.v1" />  
```  
  
## <a name="see-also"></a>関連項目  
 [ClickOnce 配置マニフェス](../deployment/clickonce-deployment-manifest.md)



