---
title: "ツール ウィンドウ、レジストリの |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: tool windows, registering
ms.assetid: c4bb8add-7148-49e4-a377-01d059fd5524
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 38b4415a24a7440a2d3725fb1183863e7a337bbb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="tool-windows-in-the-registry"></a>レジストリのツール ウィンドウ
ツール ウィンドウを提供する Vspackage に登録する必要があります[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]のウィンドウ プロバイダーをツールとして。 Visual Studio パッケージ テンプレートを使用して作成されたツール ウィンドウは、これが既定によって行います。 ツール ウィンドウのプロバイダーでは、既定のツール ウィンドウのサイズと場所、ツール ウィンドウ ペインとドッキング スタイルとして機能するウィンドウの GUID などの可視属性を指定するシステムのレジストリ キーがあります。  
  
 開発時に、管理されているツール ウィンドウ プロバイダーは、ソース コードに属性を追加し、生成されたアセンブリで RegPkg.exe ユーティリティを実行してツール ウィンドウを登録します。 詳細については、次を参照してください。[ツール ウィンドウを登録する](../extensibility/registering-a-tool-window.md)です。  
  
## <a name="registering-unmanaged-tool-window-providers"></a>管理されていないツール ウィンドウ プロバイダーを登録します。  
 管理されていないツール ウィンドウのプロバイダーに登録する必要があります[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]システム レジストリの ToolWindows セクションでします。 次の .reg ファイル フラグメントは、動的なツール ウィンドウを登録する方法を示しています。  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\<version number>\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}]  
@="{01069cdd-95ce-4620-ac21-ddff6c57f012}"  
"Name"="Microsoft.Samples.VisualStudio.IDE.ToolWindow.DynamicWindowPane"  
"Float"="250, 250, 410, 430"  
"DontForceCreate"=dword:00000001  
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}\Visibility]  
"{f1536ef8-92ec-443c-9ed7-fdadf150da82}"=dword:00000000  
```  
  
 上記の例の最初のキー、バージョン番号は、バージョンの[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]7.1 や 8.0 では、サブキー {f0e1e9a1-9860-484d-ad5d-367d79aabf55} は、ツール ウィンドウ ペイン (DynamicWindowPane) と既定値 {の GUID など、01069cdd-95ce-4620-ac21-ddff6c57f012} は、ツール ウィンドウを提供する VSPackage の GUID です。 Float 型と DontForceCreate サブキーの詳細については、次を参照してください。[ツール ウィンドウの表示構成](../extensibility/tool-window-display-configuration.md)です。  
  
 2 番目の省略可能なキー、ToolWindows\Visibility は、表示するようにツール ウィンドウを必要とするコマンドの Guid を指定します。 この場合、指定したコマンドではありません。 詳細については、次を参照してください。[ツール ウィンドウの表示構成](../extensibility/tool-window-display-configuration.md)です。  
  
## <a name="see-also"></a>関連項目  
 [VSPackage](../extensibility/internals/vspackages.md)