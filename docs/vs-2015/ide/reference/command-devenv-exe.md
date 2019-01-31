---
title: -Command (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /command switch
- /command Devenv switch
ms.assetid: 13c20cd6-f09d-400a-8b7b-ecc266a32cef
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 317103b514a04ca149940513e4e70c2799037e62
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54775902"
---
# <a name="command-devenvexe"></a>/Command (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] の統合開発環境 (IDE: Integrated Development Environment) を起動してから、指定のコマンドを実行します。  
  
## <a name="syntax"></a>構文  
  
```  
devenv /command CommandName  
```  
  
## <a name="arguments"></a>引数  
 `CommandName`  
 必須です。 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] コマンドの完全な名前またはエイリアスを二重引用符で囲みます。 コマンドとエイリアスの構文について詳しくは、「[Visual Studio のコマンド](../../ide/reference/visual-studio-commands.md)」をご覧ください。  
  
## <a name="remarks"></a>コメント  
 起動が完了すると、指定したコマンドが IDE で実行されます。 このスイッチを使用すると、IDE の起動時に [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] のスタート ページが表示されません。  
  
 アドインでコマンドが公開されている場合は、このスイッチを使ってコマンド ラインからアドインを起動できます。 詳細については、「[方法 :アドイン マネージャーを使用してアドインを制御する](http://msdn.microsoft.com/library/4f60444a-cb48-4cdb-8df4-941f6419aeeb)」を参照してください。  
  
## <a name="example"></a>例  
 この例では、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] を起動し、Open Favorite Files マクロを自動的に実行します。  
  
```  
devenv /command "Macros.MyMacros.Module1.OpenFavoriteFiles"  
```  
  
## <a name="see-also"></a>「  
 [Devenv コマンド ライン スイッチ](../../ide/reference/devenv-command-line-switches.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
