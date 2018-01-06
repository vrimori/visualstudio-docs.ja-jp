---
title: "&lt;customErrorReporting&gt;要素 (ClickOnce 配置) |Microsoft ドキュメント"
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
helpviewer_keywords: <customErrorReporting> element [ClickOnce deployment manifest]
ms.assetid: 7d31816e-c692-46b5-9cc9-753284b3bcda
caps.latest.revision: "6"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: b6b6726ebf45522834d916897f456952b66a3605
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltcustomerrorreportinggt-element-clickonce-deployment"></a>&lt;customErrorReporting&gt;要素 (ClickOnce 配置)
エラー発生時に表示する URI を指定します。  
  
## <a name="syntax"></a>構文  
  
```  
<customErrorReporting  
   uri  
/>  
```  
  
## <a name="remarks"></a>コメント  
 この要素は省略可能です。 これがないと[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]例外スタックを示すエラー ダイアログ ボックスが表示されます。 場合、`customErrorReporting`要素が含まれている[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]によって示される URI を代わりに表示されます、`uri`パラメーター。 ターゲット URI では、外側の例外クラス、内部例外クラスおよび内部例外メッセージをパラメーターとして含まれます。  
  
 この要素を使用すると、アプリケーションにエラー レポート機能を追加できます。 生成された URI には、エラーの種類に関する情報が含まれているため、Web サイトなど、適切なトラブルシューティングの画面の表示、およびその情報を解析できます。  
  
## <a name="example"></a>例  
 次のスニペットで示す、`customErrorReporting`要素、および生成された URI が生じる可能性があります。  
  
```  
<customErrorReporting uri=http://www.contoso.com/applications/error.asp />  
  
Example Generated Error:  
http://www.contoso.com/applications/error.asp? outer=System.Deployment.Application.InvalidDeploymentException&&inner=System.Deployment.Application.InvalidDeploymentException&&msg=The%20application%20manifest%20is%20signed,%20but%20the%20deployment%20manifest%20is%20unsigned.%20Both%20manifests%20must%20be%20either%20signed%20or%20unsigned.  
```  
  
## <a name="see-also"></a>参照  
 [ClickOnce 配置マニフェス](../deployment/clickonce-deployment-manifest.md)