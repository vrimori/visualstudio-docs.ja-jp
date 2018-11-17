---
title: 使用した分離シェルを変更します。Pkgundef ファイル |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, isolated mode%2C .pkgundef file
ms.assetid: 9cee2a20-f8ac-4d9d-aef9-068fcd9f27a4
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2266eda9b3e50d85131148d708a934835340f074
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51802695"
---
# <a name="modifying-the-isolated-shell-by-using-the-pkgundef-file"></a>使用した分離シェルを変更します。Pkgundef ファイル
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

分離シェル アプリケーションから指定されたレジストリ エントリを除外する .pkgundef ファイルを変更することができます。 通常、アプリケーションを開始するコンピューターでは、最初に、Visual Studio shell はコピー Visual Studio の既存のレジストリ エントリを使用、アプリケーションのルート レジストリ キーにします。 これには、現在インストールされている Vspackage への参照が含まれます。  
  
 分離シェル アプリケーションから、特定のレジストリ エントリを除外するには、パッケージのキーのエントリが続くアプリケーション .pkgundef ファイルに追加します。 キーとエントリは、.pkgdef ファイルと同じように表されますつまり、として [$RootKey$] または [$RootKey$\\*サブキー*] と"*エントリ*"=*値*ここで、*サブキー*に影響を与える、サブキーは、*エントリ*、エントリを削除すると*値*か`""`または`dword:00000000`します。  
  
 除外するには、だけで、レジストリ キーから複数のエントリは 1 回は、キーを一覧表示、続くを除外するには、各エントリの行。  
  
 分離シェル アプリケーションから、全体のレジストリ キーを除外するには、キー アプリケーション .pkgundef ファイルを追加するが、そのキーのレジストリ エントリを指定しません。  
  
 .Pkgundef ファイルにコメントを追加することができます。 単一行コメントは、最初の 2 つの文字として 2 つのスラッシュをいる必要があります。  
  
 たとえば、削除するため、**データベースへの接続**と**Serve r への接続**コマンドを**ツール**] メニューの [行のコメントを解除できます。  
  
```  
[$RootKey$\Packages\{8D8529D3-625D-4496-8354-3DAD630ECC1B}]  
```  
  
 行を追加します。  
  
```  
[$RootKey$\Packages\{198E76C1-34C0-424D-9957-B3EBD80265FB}]  
```  
  
 アプリケーションの .pkgundef ファイル。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio の機能のパッケージ Guid](../extensibility/package-guids-of-visual-studio-features.md)   
 [分離シェルのカスタマイズ](../extensibility/customizing-the-isolated-shell.md)

