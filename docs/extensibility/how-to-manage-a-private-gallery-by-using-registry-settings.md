---
title: "方法: レジストリ設定を使用してプライベート ギャラリーを管理 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSIX 非公開のギャラリーを管理します。"
  - "VSIX のプライベート ギャラリーの管理"
ms.assetid: 86b86442-4293-4cad-9fe2-876eef65f426
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# 方法: レジストリ設定を使用してプライベート ギャラリーを管理
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

管理者または分離シェル拡張機能の開発者の場合は、コントロール、テンプレート、およびツールでは、Visual Studio ギャラリーでは、サンプル ギャラリー、または非公開のギャラリーへのアクセスを制御できます。 ギャラリーを使用可能にするには、変更されたレジストリ キーとその値を記述した .pkgdef ファイルを作成します。  
  
## プライベート ギャラリーの管理  
 複数のコンピューターでのギャラリーへのアクセスを制御する .pkgdef ファイルを作成することができます。 このファイルは、次の形式が必要です。  
  
```  
[$RootPath$\ExtensionManager\Repositories\{UniqueGUID}]  
@={URI}  (REG_SZ)  
Disabled=0 | 1 (DWORD)  
Priority=0 (highest priority) … MaxInt (lowest priority) (DWORD) (uint)  
Protocol=Atom Feed|Sharepoint (REG_SZ)  
DisplayName={DisplayName} (REG_SZ)  
DisplayNameResourceID={ID} (REG_SZ)  
DisplayNamePackageGuid={GUID} (REG_SZ)  
  
```  
  
 `Repositories` キーは有効または無効にするギャラリーを参照します。 Visual Studio ギャラリーとサンプル ギャラリーは、次のリポジトリの Guid を使用します。  
  
-   Visual Studio ギャラリー: 0F45E408\-7995\-4375\-9485\-86B8DB553DC9  
  
-   サンプル ギャラリー: AEB9CB40\-D8E6\-4615\-B52C\-27E307F8506C  
  
 `Disabled` 値は省略可能です。 既定では、ギャラリーが有効にします。  
  
 `Priority` 値オプション\] ダイアログ ボックスで、ギャラリーが表示される順序を決定します。 Visual Studio ギャラリーは 10 の優先順位を持ち、サンプル ギャラリーには、20 の優先順位。 非公開のギャラリーは、優先度 100 から始まります。 表示される順序が、ローカライズ版の値によって決まりますがいくつかのギャラリーには、同じ優先度の値がある、 `DisplayName` 属性です。  
  
 `Protocol` に Atom ベースまたは SharePoint ベースのギャラリーが必要です。  
  
 いずれか `DisplayName`, 、またはその両方 `DisplayNameResourceID` と `DisplayNamePackageGuid`, を指定する必要があります。 All が指定した場合、 `DisplayNameResourceID` と `DisplayNamePackageGuid` ペアを使用します。  
  
## .Pkgdef ファイルを使用して Visual Studio ギャラリーを無効にします。  
 .Pkgdef ファイルでのギャラリーを無効にすることができます。 次のエントリには、Visual Studio ギャラリーが無効にします。  
  
```  
[$RootPath$\ExtensionManager\Repositories\{0F45E408-7995-4375-9485-86B8DB553DC9}]  
"Disabled"=dword:00000001  
  
```  
  
 次のエントリには、サンプル ギャラリーが無効にします。  
  
```  
[$RootPath$\ExtensionManager\Repositories\{AEB9CB40-D8E6-4615-B52C-27E307F8506C}]  
"Disabled"=dword:00000001  
  
```  
  
## 参照  
 [プライベート ギャラリー](../extensibility/private-galleries.md)