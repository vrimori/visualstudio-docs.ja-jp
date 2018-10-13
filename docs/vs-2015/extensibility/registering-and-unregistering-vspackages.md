---
title: 登録と Vspackage を登録解除 |Microsoft Docs
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
- registration, VSPackages
- VSPackages, registering
ms.assetid: e25e7a46-6a55-4726-8def-ca316f553d6b
caps.latest.revision: 36
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f5f43dd44dde41de4ecf3e34fa5e895ee0f4711f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49187617"
---
# <a name="registering-and-unregistering-vspackages"></a>VSPackage の登録と登録解除
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

属性を使用して、VSPackage の登録が、  
  
## <a name="registering-a-vspackage"></a>VSPackage を登録します。  
 マネージ Vspackage の登録を制御するのに属性を使用できます。 すべての登録情報は、.pkgdef ファイルに含まれます。 ファイル ベースの登録の詳細については、次を参照してください。 [CreatePkgDef ユーティリティ](../extensibility/internals/createpkgdef-utility.md)します。  
  
 次のコードでは、標準登録属性を使用して、VSPackage を登録する方法を示します。  
  
```csharp  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[Guid("0B81D86C-0A85-4f30-9B26-DD2616447F95")]  
public sealed class BasicPackage : Package  
{. . .}  
```  
  
## <a name="unregistering-an-extension"></a>拡張機能の登録を解除  
 多くの異なる Vspackage みる実験用インスタンスから削除する場合、実行して、**リセット**コマンド。 探して**Visual Studio の実験用インスタンスをリセット**コンピューターのスタート ページで、コマンドラインからこのコマンドを実行または。  
  
```vb  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe" /Reset /VSInstance=14.0 /RootSuffix=Exp  
```  
  
 Visual Studio の開発インスタンスにインストールされている拡張機能をアンインストールする場合を参照してください。**ツール/拡張機能と更新**、拡張機能を見つけて、クリック**アンインストール**します。  
  
 何らかの理由には、拡張機能のアンインストールでこれらのメソッドのどちらも成功すると、コマンドラインから、VSPackage アセンブリを次のように登録解除できます。  
  
```  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\regpkg” /unregister <pathToVSPackage assembly>  
```  
  
## <a name="see-also"></a>関連項目  
 [VSPackage](../extensibility/internals/vspackages.md)

