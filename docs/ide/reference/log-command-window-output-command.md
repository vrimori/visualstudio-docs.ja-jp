---
title: LogCommandWindowOutput コマンド
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- tools.logcommandwindowoutput
helpviewer_keywords:
- log Command window output command
- View.LogCommandWindowOutput command
ms.assetid: d4ecec35-5af4-4954-8d60-2cd24583fbb4
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2de9b21f55765706a56110aee84959b2003e994e
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
ms.locfileid: "33704682"
---
# <a name="log-command-window-output-command"></a>LogCommandWindowOutput コマンド
**[コマンド]** ウィンドウの入出力をすべてファイルにコピーします。

## <a name="syntax"></a>構文

```cmd
Tools.LogCommandWindowOutput [filename] [/on|/off] [/overwrite]
```

## <a name="arguments"></a>引数
 `filename`

 任意。 ログ ファイルの名前。 既定では、ユーザーのプロファイル フォルダーにファイルが作成されます。 ファイル名が既に存在する場合、ログは、既存のファイルの末尾に追加されます。 ファイルが指定されていない場合は、指定された最後のファイルが使用されます。 以前のファイルが存在しない場合、cmdline.log と呼ばれる既定のログ ファイルが作成されます。

> [!TIP]
> ログ ファイルの保存先を変更するには、ファイルの完全パスを入力します。パスに空白が含まれる場合は、パスを引用符で囲みます。


## <a name="switches"></a>スイッチ
 /on

 任意。 指定したファイルで **[コマンド]** ウィンドウのログの作成を開始し、ファイルに新しい情報を追加します。

 /off

 任意。 **[コマンド]** ウィンドウのログの作成を停止します。

 /overwrite

 任意。 `filename` 引数に指定したファイル名が既存のファイルと同じ場合は、既存のファイルが上書きされます。

## <a name="remarks"></a>コメント
 ファイルを指定しない場合、既定では、ファイル cmdline.log が作成されます。 既定では、このコマンドのエイリアスは Log です。

## <a name="examples"></a>使用例
 次の例では、新規のログ ファイル cmdlog を作成して、コマンドのログを開始します。

```cmd
>Tools.LogCommandWindowOutput cmdlog
```

 次の例では、コマンドのログを停止します。

```cmd
>Tools.LogCommandWindowOutput /off
```

 次の例では、以前のログ ファイルを使用してコマンドのログを再開します。

```cmd
>Tools.LogCommandWindowOutput /on
```

## <a name="see-also"></a>参照

- [Visual Studio のコマンド](../../ide/reference/visual-studio-commands.md)
- [コマンド ウィンドウ](../../ide/reference/command-window.md)
- [検索コマンド ボックス](../../ide/find-command-box.md)
- [Visual Studio コマンドのエイリアス](../../ide/reference/visual-studio-command-aliases.md)