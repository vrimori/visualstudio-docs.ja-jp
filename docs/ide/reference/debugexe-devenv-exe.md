---
title: -DebugExe (devenv.exe) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Devenv, /DebugExe switch
- DebugExe switch
- /DebugExe [devenv.exe]
ms.assetid: cd700006-1648-418f-924b-4b1e5c1412ab
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e0882ae58919cafae71bcb056e74533b7ce64a4e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="debugexe-devenvexe"></a>/DebugExe (devenv.exe)
指定したデバッグ対象の実行可能ファイルを開きます。  
  
## <a name="syntax"></a>構文  
  
```  
Devenv /debugexe ExecutableFile  
```  
  
## <a name="arguments"></a>引数  
 `ExecutableFile`  
 必須。 .exe ファイルのパスとファイル名。  
  
 .exe ファイルが見つからない場合、または存在しない場合、警告やエラーは表示されず、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] は通常どおり起動します。  
  
## <a name="remarks"></a>コメント  
 `ExecutableFile` パラメーターに続くどの文字列もそのファイルに引数として渡されます。  
  
## <a name="example"></a>例  
 次の例では、デバッグするために `MyApplication.exe` ファイルを開きます。  
  
```  
Devenv.exe /debugexe MyApplication.exe  
```  
  
## <a name="see-also"></a>参照  
 [Devenv コマンド ライン スイッチ](../../ide/reference/devenv-command-line-switches.md)