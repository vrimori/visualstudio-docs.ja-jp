---
title: -Log (devenv.exe)
ms.date: 12/12/2018
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
ms.openlocfilehash: e6573bb8bb6118a38266c0b76ef435c59e6ccecb
ms.sourcegitcommit: 01185dadd2fa1f9a040d2a366869f1a5e1d18e0f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/11/2019
ms.locfileid: "54227240"
---
# <a name="log-devenvexe"></a>/Log (devenv.exe)

すべてのアクティビティをトラブルシューティング用のログ ファイルに記録します。 このファイルは、`devenv /log` を少なくとも 1 回呼び出した後に表示されます。 ログ ファイルは既定で次の場所にあります。

**%APPDATA%\\Microsoft\\VisualStudio\\**\<Version\>**\\ActivityLog.xml**

ここで、<\<バージョン\>> は Visual Studio のバージョンです。 ただし、別のパスとファイル名を指定することもできます。

## <a name="syntax"></a>構文

```shell
devenv /Log NameOfLogFile
```

## <a name="arguments"></a>引数

- *NameOfLogFile*

  必須です。 保存先のログ ファイルの完全なパスと名前。

## <a name="remarks"></a>コメント

このスイッチは、その他すべてのスイッチの後、コマンド ラインの末尾に指定する必要があります。

ログは、`/Log` スイッチを指定して開いた Visual Studio のすべてのインスタンスのみを対象として記録されます。

## <a name="example"></a>例

この例では、ユーザーのホーム ディレクトリにある `MyVSLog.xml` ファイルにログが記録されます。

```shell
devenv /log "%USERPROFILE%\MyVSLog.xml"
```

## <a name="see-also"></a>関連項目

- [Devenv コマンドライン スイッチ](../../ide/reference/devenv-command-line-switches.md)