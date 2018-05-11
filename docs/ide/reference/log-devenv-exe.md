---
title: -Log (devenv.exe) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Devenv, /Log switch
- Log switch [devenv.exe]
- /Log Devenv switch
ms.assetid: ae23c4ae-2376-4fe3-b8d2-81d34e61c8ba
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8fa0fa90e904d4fb7f3e6820ce997a6a93e738f9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="log-devenvexe"></a>/Log (devenv.exe)
すべてのアクティビティをトラブルシューティング用のログ ファイルに記録します。 このファイルは、`devenv /log` を少なくとも 1 回呼び出した後に表示されます。 ログ ファイルは既定で次のものになります。  
  
 *%APPDATA%* \Microsoft\VisualStudio\\<*バージョン*>\ActivityLog.xml  
  
 ここで、<*バージョン*> は Visual Studio のバージョンです。 ただし、別のパスとファイル名を指定することもできます。  
  
## <a name="syntax"></a>構文  
  
```  
Devenv /log Path\NameOfLogFile  
```  
  
## <a name="remarks"></a>コメント  
 このスイッチは、その他すべてのスイッチの後、コマンド ラインの末尾に指定する必要があります。  
  
 ログは、/log スイッチで呼び出した Visual Studio のすべてのインスタンスを対象として記録されます。 スイッチなしで呼び出した Visual Studio のインスタンスについてはログ記録の対象外です。  
  
## <a name="see-also"></a>参照  
 [Devenv コマンド ライン スイッチ](../../ide/reference/devenv-command-line-switches.md)