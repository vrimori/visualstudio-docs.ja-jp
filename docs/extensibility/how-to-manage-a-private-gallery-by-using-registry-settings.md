---
title: '方法: レジストリ設定を使用してプライベート ギャラリーの管理 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSIX private galleries, managing
- managing VSIX private galleries
ms.assetid: 86b86442-4293-4cad-9fe2-876eef65f426
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c9631ffa4bce25752b838a78f306ddd3c2313a20
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31126784"
---
# <a name="how-to-manage-a-private-gallery-by-using-registry-settings"></a>方法: レジストリ設定を使用してプライベート ギャラリーの管理
管理者または分離シェル拡張機能の開発者の場合は、コントロール、テンプレート、およびツールでは、Visual Studio ギャラリー、サンプル ギャラリー、またはプライベート ギャラリーへのアクセスを制御できます。 ギャラリーを使用可能または利用不可にするには、変更されたレジストリ キーとその値を記述する .pkgdef ファイルを作成します。  
  
## <a name="managing-private-galleries"></a>プライベート ギャラリーの管理  
 複数のコンピューターでのギャラリーへのアクセスを制御する .pkgdef ファイルを作成することができます。 このファイルは次の形式が必要です。  
  
```  
[$RootKey$\ExtensionManager\Repositories\{UniqueGUID}]  
@={URI}  (REG_SZ)  
Disabled=0 | 1 (DWORD)  
Priority=0 (highest priority) ... MaxInt (lowest priority) (DWORD) (uint)  
Protocol=Atom Feed|Sharepoint (REG_SZ)  
DisplayName={DisplayName} (REG_SZ)  
DisplayNameResourceID={ID} (REG_SZ)  
DisplayNamePackageGuid={GUID} (REG_SZ)  
  
```  
  
 `Repositories`キーを有効または無効になっているギャラリーを参照します。 Visual Studio Gallery およびサンプル ギャラリーは、次のリポジトリの Guid を使用します。  
  
-   Visual Studio ギャラリー: 0F45E408-7995-4375-9485-86B8DB553DC9  
  
-   サンプル ギャラリー: AEB9CB40-D8E6-4615-B52C-27E307F8506C  
  
 `Disabled`値は省略可能です。 既定では、ギャラリーは有効です。  
  
 `Priority`値オプション ダイアログ ボックスで、ギャラリーが表示される順序を決定します。 Visual Studio ギャラリーには、優先度 10 とサンプル ギャラリーには、20 の優先順位。 プライベート ギャラリーは、100 の優先順位で開始します。 表示される順序が、ローカライズ版の値によって決まりますがいくつかのギャラリーには、同じ優先度の値がある、`DisplayName`属性。  
  
 `Protocol` Atom ベースまたは SharePoint ベースのギャラリーが必要です。  
  
 いずれか`DisplayName`、またはその両方`DisplayNameResourceID`と`DisplayNamePackageGuid`を指定する必要があります。 All が指定した場合、`DisplayNameResourceID`と`DisplayNamePackageGuid`ペアを使用します。  
  
## <a name="disabling-the-visual-studio-gallery-using-a-pkgdef-file"></a>.Pkgdef ファイルを使用して、Visual Studio ギャラリーの無効化  
 .Pkgdef ファイル内のギャラリーを無効にすることができます。 次のエントリには、Visual Studio ギャラリーが無効にします。  
  
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