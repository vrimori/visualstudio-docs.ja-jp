---
title: "使用して、分離シェルを変更します。Pkgundef ファイル |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, isolated mode, .pkgundef file
ms.assetid: 9cee2a20-f8ac-4d9d-aef9-068fcd9f27a4
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 9044821c2bfee0dba8ffa91f3d91afd565b8d957
ms.openlocfilehash: b49f3c5a39e82e0385aab12ef7042a6845b12664
ms.lasthandoff: 02/22/2017

---
# <a name="modifying-the-isolated-shell-by-using-the-pkgundef-file"></a>使用して、分離シェルを変更します。Pkgundef ファイル
分離シェル アプリケーションから指定されたレジストリ エントリを除外する .pkgundef ファイルを変更することができます。 通常は、初めてコンピューターでは、アプリケーションを起動、Visual Studio shell はコピー、既存の Visual Studio レジストリ エントリを使用アプリケーションのルート レジストリ キーにします。 これには、現在インストールされている VSPackages への参照が含まれます。  
  
 分離シェル アプリケーションから、特定のレジストリ エントリを除外するには、エントリで、パッケージのキーの後にアプリケーション .pkgundef ファイルに追加します。 キーとエントリは、.pkgdef ファイルと同じように表されます[$RootKey$] としてまたは [$RootKey$\\*サブキー*] と"*エントリ*"=*値*ここで、*サブキー*影響を与えるサブキー*エントリ*エントリを削除すると*値*か`""`または`dword:00000000`です。  
  
 除外するには、だけで、レジストリ キーから複数のエントリは&1; 回キーを一覧表示、続くを除外するには、各エントリの行。  
  
 全体のレジストリ キーを分離シェル アプリケーションから除外するには、アプリケーションの .pkgundef ファイルにキーを追加がそのキーのレジストリ エントリを特定できません。  
  
 .Pkgundef ファイルにコメントを追加することができます。 単一行のコメントは、最初の&2; つの文字と&2; つのスラッシュを持たなければなりません。  
  
 たとえば、削除するため、**データベースへの接続**と**配信 r への接続**にあるコマンドを**ツール**] メニューの [行のコメントを解除することができます。  
  
```  
[$RootKey$\Packages\{8D8529D3-625D-4496-8354-3DAD630ECC1B}]  
```  
  
 行を追加します。  
  
```  
[$RootKey$\Packages\{198E76C1-34C0-424D-9957-B3EBD80265FB}]  
```  
  
 アプリケーションの .pkgundef ファイルです。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio の機能のパッケージの Guid](../extensibility/package-guids-of-visual-studio-features.md)   
 [分離シェルをカスタマイズします。](../extensibility/customizing-the-isolated-shell.md)
