---
title: -SafeMode (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4c1cd4b15c3ce3462d6d49eca39fedbc64c744c7
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54767303"
---
# <a name="safemode-devenvexe"></a>/SafeMode (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] をセーフ モードで起動し、既定の環境とサービスのみを読み込みます。  
  
## <a name="syntax"></a>構文  
  
```  
devenv /SafeMode   
```  
  
## <a name="remarks"></a>コメント  
 このスイッチでは、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] が起動したときに、すべてのサード パーティ VSPackage を読み込まないようにするため、実行が安定したものになります。  
  
## <a name="description"></a>説明  
 次の例では、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] をセーフ モードで起動します。  
  
## <a name="code"></a>コード  
  
```  
Devenv.exe /SafeMode  
```  
  
## <a name="see-also"></a>「  
 [Devenv コマンド ライン スイッチ](../../ide/reference/devenv-command-line-switches.md)
