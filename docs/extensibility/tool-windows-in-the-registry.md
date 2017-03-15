---
title: "ツール ウィンドウで、レジストリ |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tool windows, registering
ms.assetid: c4bb8add-7148-49e4-a377-01d059fd5524
caps.latest.revision: 12
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: dc99605a367bb3584f9766b50aa2a4ff382656c4
ms.lasthandoff: 02/22/2017

---
# <a name="tool-windows-in-the-registry"></a>レジストリ内のツール ウィンドウ
ツール ウィンドウを提供する VSPackages に登録する必要があります[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]同様のツール ウィンドウのプロバイダー。 Visual Studio パッケージ テンプレートを使用して作成されたツール ウィンドウでは、既定で、これを実行します。 ツール ウィンドウのプロバイダーでは、既定のツール ウィンドウのサイズと場所、ツール ウィンドウとドッキング スタイルとして機能するウィンドウの GUID などの表示/非表示属性を指定するレジストリ キーをシステムがあります。  
  
 開発時に、管理されているツール ウィンドウのプロバイダーは、属性のソース コードを追加して、生成されたアセンブリで RegPkg.exe ユーティリティを実行ツール ウィンドウを登録します。 詳細については、次を参照してください。[ツール ウィンドウを登録する](../extensibility/registering-a-tool-window.md)です。  
  
## <a name="registering-unmanaged-tool-window-providers"></a>アンマネージ ツール ウィンドウのプロバイダーを登録します。  
 アンマネージ ツール ウィンドウのプロバイダーに登録する必要があります[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]システム レジストリの ToolWindows セクションにします。 次の .reg ファイル フラグメントは、動的なツール ウィンドウを登録する方法を示しています。  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\<version number>\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}]  
@="{01069cdd-95ce-4620-ac21-ddff6c57f012}"  
"Name"="Microsoft.Samples.VisualStudio.IDE.ToolWindow.DynamicWindowPane"  
"Float"="250, 250, 410, 430"  
"DontForceCreate"=dword:00000001  
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}\Visibility]  
"{f1536ef8-92ec-443c-9ed7-fdadf150da82}"=dword:00000000  
```  
  
 上記の例で最初のキー、バージョン番号は、バージョンの[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]7.1 8.0 など {f0e1e9a1-9860-484d-ad5d-367d79aabf55} サブキーには、ツール ウィンドウ ペイン (DynamicWindowPane) の GUID、および {01069cdd-95ce-4620-ac21-ddff6c57f012} の既定値は、ツール ウィンドウを提供する VSPackage の GUID。 浮動小数点演算と DontForceCreate サブキーの詳細については、次を参照してください。[ツール ウィンドウの表示構成](../extensibility/tool-window-display-configuration.md)します。  
  
 2 番目のオプションのキー、ToolWindows\Visibility では、参照できるように、ツール ウィンドウを必要とするコマンドの Guid を指定します。 この場合は、指定されたコマンドではありません。 詳細については、次を参照してください。[ツール ウィンドウの表示構成](../extensibility/tool-window-display-configuration.md)します。  
  
## <a name="see-also"></a>関連項目  
 [VSPackage の基本事項](../misc/vspackage-essentials.md)
