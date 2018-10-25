---
title: Vspackage のリソース |Microsoft Docs
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
- managed VSPackages, resources in
- resources, managed VSPackages
- VSPackages, managed resources
ms.assetid: cc8c17a6-b190-4856-b001-0c1104f104b2
caps.latest.revision: 24
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d032863677a24f377da8068b4a6e5565c5a2241c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49830679"
---
# <a name="resources-in-vspackages"></a>VSPackage のリソース
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

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
  
  使用することができます、<xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>に示すために属性[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]マネージ リソースが使用できることです。  
  
  [!code-csharp[VSSDKResources#1](../../snippets/csharp/VS_Snippets_VSSDK/vssdkresources/cs/vssdkresourcespackage.cs#1)]
  [!code-vb[VSSDKResources#1](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdkresources/vb/vssdkresourcespackage.vb#1)]  
  
  設定<xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>こうすることを示します[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]を使用して、リソースについては、検索するときは、アンマネージ サテライト Dll を無視する必要があります<xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackageString%2A>します。 場合[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]リソース ID が同じである 2 つ以上のリソースが検出した見つけた最初のリソースを使用します。  
  
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
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 可能であれば、Vspackage の読み込みを遅延します。 VSPackage で CTO ファイルを埋め込み、結果を[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]コマンドがマージされたテーブルを作成する場合は、セットアップ中にメモリ内でこのようなすべての Vspackage を読み込む必要があります。 VSPackage でコードを実行することがなく、メタデータを調べることで、VSPackage からリソースを抽出できます。 パフォーマンスの低下はごくわずかであるため、VSPackage ではこの時点で初期化されていません。  
  
 ときに[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]セットアップ後の VSPackage からリソースを要求、パッケージが既に読み込まれ、初期化される可能性が高いため、パフォーマンスの低下はごくわずかです。  
  
## <a name="see-also"></a>関連項目  
 [マネージ Vspackage](../../misc/managed-vspackages.md)   
 [Vspackage の管理](../../extensibility/managing-vspackages.md)   
 [MFC アプリケーションのローカライズされたリソース: サテライト Dll](http://msdn.microsoft.com/library/3a1100ae-a9c8-47b5-adbd-cbedef5992ef)   
 [マネージド VSPackage](../../misc/managed-vspackages.md)

