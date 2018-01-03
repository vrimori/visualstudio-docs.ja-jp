---
title: -SafeMode (devenv.exe) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
caps.latest.revision: "5"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 17a8d92075f558e1e00bbba04f2c3ae955056b61
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="safemode-devenvexe"></a>/SafeMode (devenv.exe)
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] をセーフ モードで起動し、既定の環境とサービスのみを読み込みます。  
  
## <a name="syntax"></a>構文  
  
```  
devenv /SafeMode   
```  
  
## <a name="remarks"></a>コメント  
 このスイッチでは、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] が起動したときに、すべてのサード パーティ VSPackage を読み込まないようにするため、実行が安定したものになります。  
  
## <a name="description"></a>説明  
 次の例では、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] をセーフ モードで起動します。  
  
## <a name="code"></a>コード  
  
```  
Devenv.exe /SafeMode  
```  
  
## <a name="see-also"></a>参照  
 [Devenv コマンド ライン スイッチ](../../ide/reference/devenv-command-line-switches.md)