---
title: "登録および VSPackages を登録解除 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: e25e7a46-6a55-4726-8def-ca316f553d6b
caps.latest.revision: 35
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 73039d6e9bf0db6b3deee00745e21660173f21c0
ms.contentlocale: ja-jp
ms.lasthandoff: 02/22/2017

---
# <a name="registering-and-unregistering-vspackages"></a>Vspackage の登録と登録解除しています
属性を使用して、VSPackage を登録するが、  
  
## <a name="registering-a-vspackage"></a>VSPackage を登録します。  
 マネージ VSPackages の登録を制御するのに属性を使用することができます。 すべての登録情報は、.pkgdef ファイルに含まれます。 ファイル ベースの登録の詳細については、次を参照してください。 [CreatePkgDef ユーティリティ](../extensibility/internals/createpkgdef-utility.md)します。  
  
 次のコードでは、標準登録属性を使用して、VSPackage を登録する方法を示します。  
  
```c#  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[Guid("0B81D86C-0A85-4f30-9B26-DD2616447F95")]  
public sealed class BasicPackage : Package  
{. . .}  
```  
  
## <a name="unregistering-an-extension"></a>拡張機能の登録を解除します。  
 実行できますだけを実験して多数の異なる VSPackages きましたし、実験用インスタンスから削除する場合、**リセット**コマンドです。 探します**Visual Studio の実験用インスタンスをリセット**コンピューターのスタート ページに、またはコマンドラインからこのコマンドを実行します。  
  
```vb  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe" /Reset /VSInstance=14.0 /RootSuffix=Exp  
```  
  
 Visual Studio の開発インスタンスにインストールした拡張機能をアンインストールする場合に、**ツール/拡張機能と更新プログラム**、拡張機能を見つけて、クリックして**アンインストール**します。  
  
 何らかの理由で、拡張機能をアンインストールするこれらのメソッドのどちらも成功すると、コマンドラインから VSPackage アセンブリを次のように登録解除できます。  
  
```  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\regpkg" /unregister <pathToVSPackage assembly>  
```  
  
## <a name="see-also"></a>関連項目  
 [Vspackages にあります。](../extensibility/internals/vspackages.md)
