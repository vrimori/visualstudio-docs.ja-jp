---
title: -Edit (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- Devenv, /edit switch
- /Edit Devenv switch
ms.assetid: 02b3d6e7-a2b1-4d83-a747-aa8c2fb758b7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0ccbd3a693313b870378021e6404424cfb11f199
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53907989"
---
# <a name="edit-devenvexe"></a>/Edit (devenv.exe)
指定されたファイルを [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] の既存のインスタンスで開きます。

## <a name="syntax"></a>構文

```cmd
Devenv /edit [file1[ file2]]
```

## <a name="arguments"></a>引数
 `file1`

 任意。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] の既存のインスタンスで開くファイル。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] のインスタンスが存在していない場合は、簡略化されたウィンドウ レイアウトで新しいインスタンスが作成され、新しいインスタンスで `file1` が開かれます。

 `file2`

 任意。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] の既存インスタンスで開く 1 つ以上の追加ファイル。

## <a name="remarks"></a>コメント
 ファイルが指定されておらず、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] の既存のインスタンスがある場合は、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] の既存のインスタンスがフォーカスを取得します。 ファイルが指定されておらず、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] の既存のインスタンスがない場合は、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] の新しいインスタンスが簡略化されたウィンドウ レイアウトで作成されます。

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] の既存のインスタンスがモーダル状態の場合 (たとえば、[[オプション] ダイアログ ボックス](../../ide/reference/options-dialog-box-visual-studio.md)が開かれている場合)、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] がモーダル状態を終了すると、ファイルが既存のインスタンスで開かれます。

## <a name="example"></a>例
 この例では、ファイル `MyFile.cs` が [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] の既存インスタンスで開かれるか、またはインスタンスがまだ存在しない場合は [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] の新しいインスタンスでファイルが開かれます。

```cmd
devenv /edit MyFile.cs
```

## <a name="see-also"></a>「

- [Devenv コマンドライン スイッチ](../../ide/reference/devenv-command-line-switches.md)