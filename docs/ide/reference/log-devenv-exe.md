---
title: -Log (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
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
ms.openlocfilehash: 3373f1e1a23ae0373a9c49a39a924398ebe143e0
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
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

## <a name="see-also"></a>参照

- [Devenv コマンド ライン スイッチ](../../ide/reference/devenv-command-line-switches.md)