---
title: -DebugExe (devenv.exe) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Devenv, /DebugExe switch
- DebugExe switch
- /DebugExe [devenv.exe]
ms.assetid: cd700006-1648-418f-924b-4b1e5c1412ab
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f58db37f353cddd7444e7ea185dc07c0ec6cd603
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47533788"
---
# <a name="debugexe-devenvexe"></a>/DebugExe (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[DebugExe (devenv.exe)](https://docs.microsoft.com/visualstudio/ide/reference/debugexe-devenv-exe)します。  
  
  
指定したデバッグ対象の実行可能ファイルを開きます。  
  
## <a name="syntax"></a>構文  
  
```  
Devenv /debugexe ExecutableFile  
```  
  
## <a name="arguments"></a>引数  
 `ExecutableFile`  
 必須。 .exe ファイルのパスとファイル名。  
  
 .exe ファイルが見つからない場合、または存在しない場合、警告やエラーは表示されず、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] は通常どおり起動します。  
  
## <a name="remarks"></a>Remarks  
 `ExecutableFile` パラメーターに続くどの文字列もそのファイルに引数として渡されます。  
  
## <a name="example"></a>例  
 次の例では、デバッグするために `MyApplication.exe` ファイルを開きます。  
  
```  
Devenv.exe /debugexe MyApplication.exe  
```  
  
## <a name="see-also"></a>関連項目  
 [Devenv コマンド ライン スイッチ](../../ide/reference/devenv-command-line-switches.md)



