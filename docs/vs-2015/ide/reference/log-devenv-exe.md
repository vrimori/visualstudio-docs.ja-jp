---
title: -Log (devenv.exe) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Devenv, /Log switch
- Log switch [devenv.exe]
- /Log Devenv switch
ms.assetid: ae23c4ae-2376-4fe3-b8d2-81d34e61c8ba
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6e3c8ee5d8c0bc5d68159fe0b40f22dda74f564f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49292033"
---
# <a name="log-devenvexe"></a>/Log (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
すべてのアクティビティをトラブルシューティング用のログ ファイルに記録します。 このファイルは、`devenv /log` を少なくとも 1 回呼び出した後に表示されます。 ログ ファイルは既定で次のものになります。  
  
 *%APPDATA%* \Microsoft\VisualStudio\\<*バージョン*>\ActivityLog.xml  
  
 ここで、<*バージョン*> は Visual Studio のバージョンです。 ただし、別のパスとファイル名を指定することもできます。  
  
## <a name="syntax"></a>構文  
  
```  
Devenv /log Path\NameOfLogFile  
```  
  
## <a name="remarks"></a>Remarks  
 このスイッチは、その他すべてのスイッチの後、コマンド ラインの末尾に指定する必要があります。  
  
 ログは、/log スイッチで呼び出した Visual Studio のすべてのインスタンスを対象として記録されます。 スイッチなしで呼び出した Visual Studio のインスタンスについてはログ記録の対象外です。  
  
## <a name="see-also"></a>関連項目  
 [Devenv コマンド ライン スイッチ](../../ide/reference/devenv-command-line-switches.md)



