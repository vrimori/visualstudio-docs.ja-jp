---
title: -Command (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /command switch
- /command Devenv switch
ms.assetid: 13c20cd6-f09d-400a-8b7b-ecc266a32cef
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f2ee6f1166a543cc3dc85dfb62d19d1c5b194a16
ms.sourcegitcommit: 54c65f81a138fc1e8ff1826f7bd9dcec710618cc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/19/2018
ms.locfileid: "51948167"
---
# <a name="command-devenvexe"></a>/Command (devenv.exe)
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] の統合開発環境 (IDE: Integrated Development Environment) を起動してから、指定のコマンドを実行します。

## <a name="syntax"></a>構文

```cmd
devenv /command CommandName
```

## <a name="arguments"></a>引数
 `CommandName` 必須。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] コマンドの完全な名前またはエイリアスを二重引用符で囲みます。 コマンドとエイリアスの構文について詳しくは、「[Visual Studio のコマンド](../../ide/reference/visual-studio-commands.md)」をご覧ください。

## <a name="remarks"></a>コメント
 起動が完了すると、指定したコマンドが IDE で実行されます。 このスイッチを使用すると、IDE の起動時に [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] のスタート ページが表示されません。

 アドインでコマンドが公開されている場合は、このスイッチを使ってコマンド ラインからアドインを起動できます。 詳しくは、「[方法: アドイン マネージャーを使用してアドインを制御する](https://msdn.microsoft.com/Library/4f60444a-cb48-4cdb-8df4-941f6419aeeb)」をご覧ください。

## <a name="example"></a>例
 この例では、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] を起動し、Open Favorite Files マクロを自動的に実行します。

```cmd
devenv /command "Macros.MyMacros.Module1.OpenFavoriteFiles"
```

## <a name="see-also"></a>参照

- [Devenv コマンドライン スイッチ](../../ide/reference/devenv-command-line-switches.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)