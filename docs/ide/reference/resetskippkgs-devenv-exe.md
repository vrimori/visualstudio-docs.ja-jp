---
title: -ResetSkipPkgs (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /ResetSkipPkgs Devenv switch
- Devenv, /ResetSkipPkgs switch
- ResetSkipPkgs switch
ms.assetid: 7ece64f9-cfa4-4b34-b0d9-1c338b9557b3
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5f797b6228124da8d8a998a6647dcfd9195ea92c
ms.sourcegitcommit: 54c65f81a138fc1e8ff1826f7bd9dcec710618cc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/19/2018
ms.locfileid: "51948076"
---
# <a name="resetskippkgs-devenvexe"></a>/ResetSkipPkgs (devenv.exe)
問題のある VSPackage の読み込みを避けるためにユーザーによって VSPackage に追加された、読み込みを省略するためのオプションをすべてクリアします。その後、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] を起動させます。

## <a name="syntax"></a>構文

```cmd
Devenv /ResetSkipPkgs
```

## <a name="remarks"></a>コメント
 SkipLoading タグがあると、VSPackage の読み込みが無効になります。タグをクリアすると、VSPackage の読み込みが再度有効になります。

## <a name="example"></a>例
 次の例では、すべての SkipLoading タグをクリアします。

```cmd
Devenv.exe /ResetSkipPkgs
```

## <a name="see-also"></a>参照

- [Devenv コマンドライン スイッチ](../../ide/reference/devenv-command-line-switches.md)