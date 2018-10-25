---
title: -Command (devenv.exe) | Microsoft Docs
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
- Devenv, /command switch
- /command Devenv switch
ms.assetid: 13c20cd6-f09d-400a-8b7b-ecc266a32cef
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5f95d8758da77f1b720f0a1b6ca74f7ac753d805
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49254385"
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
 必須。 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] コマンドの完全な名前またはエイリアスを二重引用符で囲みます。 コマンドとエイリアスの構文について詳しくは、「[Visual Studio のコマンド](../../ide/reference/visual-studio-commands.md)」をご覧ください。  
  
## <a name="remarks"></a>Remarks  
 起動が完了すると、指定したコマンドが IDE で実行されます。 このスイッチを使用すると、IDE の起動時に [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] のスタート ページが表示されません。  
  
 アドインでコマンドが公開されている場合は、このスイッチを使ってコマンド ラインからアドインを起動できます。 詳しくは、「[方法: アドイン マネージャーを使用してアドインを制御する](http://msdn.microsoft.com/library/4f60444a-cb48-4cdb-8df4-941f6419aeeb)」をご覧ください。  
  
## <a name="example"></a>例  
 この例では、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] を起動し、Open Favorite Files マクロを自動的に実行します。  
  
```  
devenv /command "Macros.MyMacros.Module1.OpenFavoriteFiles"  
```  
  
## <a name="see-also"></a>関連項目  
 [Devenv コマンド ライン スイッチ](../../ide/reference/devenv-command-line-switches.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)



