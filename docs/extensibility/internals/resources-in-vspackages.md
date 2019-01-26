---
title: Vspackage のリソース |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, resources in
- resources, managed VSPackages
- VSPackages, managed resources
ms.assetid: cc8c17a6-b190-4856-b001-0c1104f104b2
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dcb47398b4627558c6f00935b1e7819f06ed6302
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54935086"
---
# <a name="resources-in-vspackages"></a>VSPackage のリソース
ネイティブ UI、サテライト Dll マネージ サテライト Dll、または、マネージ VSPackage 自体には、ローカライズされたリソースを埋め込むことができます。  
  
 Vspackage では、一部のリソースを埋め込むことができません。 次のマネージ型を埋め込むことができます。  
  
- 文字列  
  
- (これはまた、文字列) パッケージ ロード キー  
  
- ツール ウィンドウのアイコン  
  
- コンパイル済みのコマンド テーブルの出力 (CTO) ファイル  
  
- CTO ビットマップ  
  
- コマンド ライン ヘルプ  
  
- ダイアログ ボックスのデータについて  
  
  リソース ID を管理対象のパッケージ内のリソースが選択されています。 CTMENU 名前を指定する必要があります、CTO ファイルは例外です。 CTO ファイルとしてリソース テーブルには表示する必要があります、`byte[]`します。 その他のすべてのリソース項目は、型によって識別されます。  
  
  使用することができます、<xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>に示すために属性[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]マネージ リソースが使用できることです。  
  
  [!code-csharp[VSSDKResources#1](../../extensibility/internals/codesnippet/CSharp/resources-in-vspackages_1.cs)]
  [!code-vb[VSSDKResources#1](../../extensibility/internals/codesnippet/VisualBasic/resources-in-vspackages_1.vb)]  
  
  設定<xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>こうすることを示します[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]を使用して、リソースについては、検索するときは、アンマネージ サテライト Dll を無視する必要があります<xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackageString%2A>します。 場合[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]リソース ID が同じである 2 つ以上のリソースが検出した見つけた最初のリソースを使用します。  
  
## <a name="example"></a>例  
 次の例は、ツール ウィンドウ アイコンのマネージ表現です。  
  
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
  
 次の例では、CTMENU 名前を指定する必要があります、CTO バイト配列を埋め込む方法を示します。  
  
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
  
## <a name="implementation-notes"></a>実装に関する注意事項  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 可能であれば、Vspackage の読み込みを遅延します。 VSPackage で CTO ファイルを埋め込み、結果を[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]コマンドがマージされたテーブルを作成する場合は、セットアップ中にメモリ内でこのようなすべての Vspackage を読み込む必要があります。 VSPackage でコードを実行することがなく、メタデータを調べることで、VSPackage からリソースを抽出できます。 パフォーマンスの低下はごくわずかであるため、VSPackage ではこの時点で初期化されていません。  
  
 ときに[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]セットアップ後の VSPackage からリソースを要求、パッケージが既に読み込まれ、初期化される可能性が高いため、パフォーマンスの低下はごくわずかです。  
  
## <a name="see-also"></a>関連項目  
 [Vspackage の管理](../../extensibility/managing-vspackages.md)   
 [MFC アプリケーションのローカライズされたリソース:サテライト DLL](/cpp/build/localized-resources-in-mfc-applications-satellite-dlls)   
