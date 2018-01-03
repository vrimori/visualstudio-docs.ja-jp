---
title: -ResetSkipPkgs (devenv.exe) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- /ResetSkipPkgs Devenv switch
- Devenv, /ResetSkipPkgs switch
- ResetSkipPkgs switch
ms.assetid: 7ece64f9-cfa4-4b34-b0d9-1c338b9557b3
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 3f84b4a8f73d378629edcf862f1aa53aa478fa1a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="resetskippkgs-devenvexe"></a>/ResetSkipPkgs (devenv.exe)
問題のある VSPackage の読み込みを避けるためにユーザーによって VSPackage に追加された、読み込みを省略するためのオプションをすべてクリアします。その後、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] を起動させます。  
  
## <a name="syntax"></a>構文  
  
```  
Devenv /ResetSkipPkgs  
```  
  
## <a name="remarks"></a>コメント  
 SkipLoading タグがあると、VSPackage の読み込みが無効になります。タグをクリアすると、VSPackage の読み込みが再度有効になります。  
  
## <a name="example"></a>例  
 次の例では、すべての SkipLoading タグをクリアします。  
  
```  
Devenv.exe /ResetSkipPkgs  
```  
  
## <a name="see-also"></a>参照  
 [Devenv コマンド ライン スイッチ](../../ide/reference/devenv-command-line-switches.md)