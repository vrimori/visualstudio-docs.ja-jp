---
title: "&lt;説明&gt;要素 (ClickOnce 配置) |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: urn:schemas-microsoft-com:asm.v2#description
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords: <description> element [ClickOnce deployment manifest]
ms.assetid: 18f6919e-a3ab-4942-a57d-167fabfac44e
caps.latest.revision: "19"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: f5045f9203d5413efdd6d192d2667e94d0119220
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltdescriptiongt-element-clickonce-deployment"></a>&lt;説明&gt;要素 (ClickOnce 配置)
シェルに表示を作成するためのアプリケーション情報を識別し、**プログラム追加と削除**コントロール パネル内の項目。  
  
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
 `description` 要素は必須です。この要素は `urn:schemas-microsoft-com:asm.v1` 名前空間に属します。 これは、子要素が含まれていない、次の属性です。  
  
|属性|説明|  
|---------------|-----------------|  
|`publisher`|必須。 Windows のアイコンの配置に使用する会社名を識別**開始**メニューおよび**プログラム追加と削除**インストールの展開を構成すると、コントロール パネル内の項目。|  
|`product`|必須。 完全な製品名を識別します。 Windows にインストールされているアイコンのタイトルとして使用されている**開始**メニュー。|  
|`suiteName`|任意。 内のサブフォルダーを識別、 `publisher` windows フォルダー**開始**メニュー。|  
|`supportUrl`|任意。 表示されるサポートの URL を指定します、**プログラム追加と削除**コントロール パネル内の項目。 この URL へのショートカットが、Windows のアプリケーションのサポートの作成も**開始**] メニューの [インストールの展開を構成するとします。|  
  
## <a name="remarks"></a>コメント  
 Description 要素と、すべての展開構成が必要です。  
  
## <a name="example"></a>例  
 次のコード例を示しています、`description`内の要素、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]配置マニフェスト。 このコード例に示されている例の一部である、 [ClickOnce 配置マニフェスト](../deployment/clickonce-deployment-manifest.md)トピックです。  
  
```  
<description   
  asmv2:publisher="My Company Name"  
  asmv2:product="My Application"  
  xmlns="urn:schemas-microsoft-com:asm.v1" />  
```  
  
## <a name="see-also"></a>参照  
 [ClickOnce 配置マニフェス](../deployment/clickonce-deployment-manifest.md)