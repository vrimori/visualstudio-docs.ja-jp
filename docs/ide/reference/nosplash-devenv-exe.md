---
title: -NoSplash (devenv.exe)
ms.date: 12/10/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /NoSplash switch
- /NoSplash Devenv switch
- NoSplash Devenv switch
author: DennisLee-DennisLee
ms.author: v-dele
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f11b44833ae54c6982cc4df9e2dbd6cb03e7fcd1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54927894"
---
# <a name="nosplash-devenvexe"></a>/NoSplash (devenv.exe)

スプラッシュ スクリーンが表示されないようにします。

## <a name="syntax"></a>構文

```shell
devenv /NoSplash [File1[ FileN]...]
```

## <a name="arguments"></a>引数

- *File1*

  任意。 Visual Studio の既存のインスタンスで開くファイル。 Visual Studio のインスタンスが存在していない場合は、簡略化されたウィンドウ レイアウトで新しいインスタンスが作成され、その新しいインスタンスで *File1* が開かれます。

- *FileN*

  任意。 Visual Studio の既存インスタンスで開く 1 つ以上の追加ファイル。

## <a name="remarks"></a>コメント

このスイッチを指定すると、スプラッシュ スクリーンが非表示になります。 このスイッチをオフのままにすると、スプラッシュ スクリーンが表示されます。 スプラッシュ スクリーンをさらに詳しく調べるには (たとえば、VSPackage 製品アイコンを確認する場合)、[/Splash](../../extensibility/devenv-command-line-switches-for-vspackage-development.md) スイッチを使用します。

`/NoSplash` スイッチは、[/Run](run-devenv-exe.md) または [/DebugExe](debugexe-devenv-exe.md) など、他のスイッチと組み合わせることができます。

## <a name="example"></a>例

この 3 つの例では、いずれもスプラッシュ スクリーンを表示せずに IDE を開きます。 2 つ目の例でも、指定されたソリューションをコンパイルしてビルドされた実行可能ファイルを実行します。 3 つ目の例では、IDE でデバッグするために指定された実行可能ファイルを開きます。

```shell
devenv /nosplash

devenv /nosplash /run MySolution.sln

devenv /nosplash /debugexe MySolution.exe
```

## <a name="see-also"></a>関連項目

- [Devenv コマンドライン スイッチ](../../ide/reference/devenv-command-line-switches.md)
- [VSPackage 開発の Devenv コマンド ライン スイッチ](../../extensibility/devenv-command-line-switches-for-vspackage-development.md)
