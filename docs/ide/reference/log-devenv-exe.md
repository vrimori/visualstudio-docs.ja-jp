---
title: -Log (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
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
ms.openlocfilehash: b0d2e6af25b4e0acc4aad88c33861e9d22a775b4
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53846127"
---
# <a name="log-devenvexe"></a>/Log (devenv.exe)
すべてのアクティビティをトラブルシューティング用のログ ファイルに記録します。 このファイルは、`devenv /log` を少なくとも 1 回呼び出した後に表示されます。 ログ ファイルは既定で次のものになります。

 *%APPDATA%* \Microsoft\VisualStudio\\<*バージョン*>\ActivityLog.xml

 ここで、<*バージョン*> は Visual Studio のバージョンです。 ただし、別のパスとファイル名を指定することもできます。

## <a name="syntax"></a>構文

```cmd
Devenv /log Path\NameOfLogFile
```

## <a name="remarks"></a>コメント
 このスイッチは、その他すべてのスイッチの後、コマンド ラインの末尾に指定する必要があります。

 ログは、/log スイッチで呼び出した Visual Studio のすべてのインスタンスを対象として記録されます。 スイッチなしで呼び出した Visual Studio のインスタンスについてはログ記録の対象外です。

## <a name="see-also"></a>「

- [Devenv コマンドライン スイッチ](../../ide/reference/devenv-command-line-switches.md)