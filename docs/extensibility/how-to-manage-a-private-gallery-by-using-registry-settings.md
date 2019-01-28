---
title: '方法: レジストリ設定を使用してプライベート ギャラリーの管理 |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSIX private galleries, managing
- managing VSIX private galleries
ms.assetid: 86b86442-4293-4cad-9fe2-876eef65f426
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5d75976ba9c677bb9b8f6c32623f81834471e10a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55021521"
---
# <a name="how-to-manage-a-private-gallery-by-using-registry-settings"></a>方法: レジストリ設定を使用してプライベート ギャラリーを管理します。
管理者または開発者の分離シェルの拡張機能の場合は、コントロール、テンプレート、およびツールでは、Visual Studio ギャラリーでは、サンプル ギャラリー、またはプライベート ギャラリーへのアクセスを制御できます。 ギャラリーを使用できないか使用できなくするために、作成、 *.pkgdef*ファイルを変更したレジストリ キーとその値について説明します。  
  
## <a name="manage-private-galleries"></a>プライベート ギャラリーを管理します。  
 作成することができます、 *.pkgdef*ファイルを複数のコンピューターでギャラリーへのアクセスを制御します。 このファイルは、次の形式をいる必要があります。  
  
```  
[$RootKey$\ExtensionManager\Repositories\{UniqueGUID}]  
@={URI}  (REG_SZ)  
Disabled=0 | 1 (DWORD)  
Priority=0 (highest priority) ... MaxInt (lowest priority) (DWORD) (uint)  
Protocol=Atom Feed|Sharepoint (REG_SZ)  
DisplayName={DisplayName} (REG_SZ)  
DisplayNameResourceID={ID} (REG_SZ)  
DisplayNamePackageGuid={GUID} (REG_SZ)  
  
```  
  
 `Repositories`キーは有効または無効にするギャラリーを参照します。 Visual Studio ギャラリーとサンプル ギャラリーは、次のリポジトリの Guid を使用します。  
  
- Visual Studio ギャラリー:0F45E408-7995-4375-9485-86B8DB553DC9  
  
- サンプル ギャラリー:AEB9CB40-D8E6-4615-B52C-27E307F8506C  
  
  `Disabled`値は省略可能です。 既定では、ギャラリーが有効にします。  
  
  `Priority`値内で、ギャラリーが表示される順序を決定、**オプション** ダイアログ ボックス。 Visual Studio ギャラリーが 10 の優先順位とサンプル ギャラリーが 20 の優先順位。 プライベート ギャラリーは、優先度 100 から始まります。 表示される順序が、ローカライズ済みの値によって決まりますがいくつかのギャラリーには、同じ優先順位の値がある、`DisplayName`属性。  
  
  `Protocol`値が Atom ベースまたは SharePoint ベースのギャラリーが必要です。  
  
  いずれか`DisplayName`、またはその両方`DisplayNameResourceID`と`DisplayNamePackageGuid`を指定する必要があります。 All が指定した場合、`DisplayNameResourceID`と`DisplayNamePackageGuid`ペアを使用します。  
  
## <a name="disable-the-visual-studio-gallery-using-a-pkgdef-file"></a>.Pkgdef ファイルを使用して、Visual Studio ギャラリーを無効にします。  
 ギャラリーを無効にすることができます、 *.pkgdef*ファイル。 次のエントリには、Visual Studio ギャラリーが無効にします。  
  
```  
[$RootKey$\ExtensionManager\Repositories\{0F45E408-7995-4375-9485-86B8DB553DC9}]  
"Disabled"=dword:00000001  
  
```  
  
 次のエントリには、サンプル ギャラリーが無効にします。  
  
```  
[$RootKey$\ExtensionManager\Repositories\{AEB9CB40-D8E6-4615-B52C-27E307F8506C}]  
"Disabled"=dword:00000001  
  
```  
  
## <a name="see-also"></a>関連項目  
 [プライベート ギャラリー](../extensibility/private-galleries.md)