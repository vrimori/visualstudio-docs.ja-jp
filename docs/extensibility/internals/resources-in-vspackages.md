---
title: Vspackage のリソース |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, resources in
- resources, managed VSPackages
- VSPackages, managed resources
ms.assetid: cc8c17a6-b190-4856-b001-0c1104f104b2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d252f61a9f634f4bb8435626c41c586bbe5cb839
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="resources-in-vspackages"></a>Vspackage のリソース
ネイティブ UI、サテライト Dll マネージ サテライト Dll の場合、または、マネージ VSPackage 自体には、ローカライズされたリソースを埋め込むことができます。  
  
 一部のリソースは、Vspackage に埋め込むことはできません。 次のマネージ型を埋め込むことができます。  
  
-   文字列  
  
-   (これは文字列ではまた) パッケージ ロード キー  
  
-   ツール ウィンドウ アイコン  
  
-   コンパイル済みのコマンド テーブルの出力 (CTO) ファイル  
  
-   CTO ビットマップ  
  
-   コマンドラインのヘルプ  
  
-   ダイアログ ボックスのデータについて  
  
 マネージ パッケージでのリソースのリソース ID を選択します。 という名前に CTMENU CTO ファイルには例外です。 CTO ファイルが、リソース テーブルとしてに表示する必要があります、`byte[]`です。 その他のすべてのリソース アイテムは、型で識別されます。  
  
 使用することができます、<xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>に示す属性[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]マネージ リソースが利用できることです。  
  
 [!code-csharp[VSSDKResources#1](../../extensibility/internals/codesnippet/CSharp/resources-in-vspackages_1.cs)]
 [!code-vb[VSSDKResources#1](../../extensibility/internals/codesnippet/VisualBasic/resources-in-vspackages_1.vb)]  
  
 設定<xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>このようなことを示します[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]を使用して、リソースについては、検索するときに、アンマネージ サテライト Dll を無視する必要があります<xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackageString%2A>です。 場合[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]同じリソース ID を持つ 2 つ以上のリソースを検出したが見つかった最初のリソースを使用します。  
  
## <a name="example"></a>例  
 次の例は、ツール ウィンドウ アイコンの管理された表現です。  
  
```  
<data name="1001"  
type="System.Resources.ResXFileRef,System.Windows.Forms">  
     <value>  
     MyToolWinIcon.bmp;  
     System.Drawing.Bitmap,  
     System.Drawing,  
     Version=1.0.0.0,  
     Culture=neutral,  
     PublicKeyToken=b03f5f7f11d50a3a  
     </value>  
</data>  
```  
  
 次の例では、という名前に CTMENU、CTO バイト配列を埋め込む方法を示します。  
  
```  
<data name="CTMENU"  
type="System.Resources.ResXFileRef,System.Windows.Forms">  
     <value>  
     MyPackage.cto;  
     System.Byte[],  
     mscorlib,  
     Version=1.0.0.0,  
     Culture=neutral,  
     PublicKeyToken=b03f5f7f11d50a3a  
     </value>  
</data>  
```  
  
## <a name="implementation-notes"></a>実装に関するメモ  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 可能な限り、Vspackage の遅延読み込みします。 VSPackage で CTO ファイルを埋め込みの結果は[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]マージ コマンド テーブルを作成するときに、セットアップ中にメモリ内でこのようなすべての Vspackage を読み込む必要があります。 リソースは、VSPackage でコードを実行しなくても、メタデータを調べることで、VSPackage から抽出できます。 パフォーマンスの低下を最小限に抑えるため、VSPackage ではこの時点で初期化されていません。  
  
 ときに[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]セットアップ後の VSPackage からリソースを要求、パッケージが既に読み込まれ、初期化、可能性の高いパフォーマンスの低下を最小限に抑えるようにします。  
  
## <a name="see-also"></a>関連項目  
 [Vspackage の管理](../../extensibility/managing-vspackages.md)   
 [MFC アプリケーションのローカライズされたリソース: サテライト DLL](/cpp/build/localized-resources-in-mfc-applications-satellite-dlls)   
