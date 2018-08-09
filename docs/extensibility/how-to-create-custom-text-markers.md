---
title: '方法: カスタム テキスト マーカーの作成 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - custom text markers
ms.assetid: 6e32ed81-c604-4a32-9012-8db3bec7c846
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fc86f6f5e6689903acb4c57131cee5562117f732
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/08/2018
ms.locfileid: "39636348"
---
# <a name="how-to-create-custom-text-markers"></a>方法: カスタム テキスト マーカーの作成
強調したり、コードを整理するカスタム テキスト マーカーを作成する場合は、以下の手順を実行する必要があります。  
  
-   その他のツールがアクセスできるように、新しいテキスト マーカーを登録します。  
  
-   テキスト マーカーの構成を既定の実装を提供します。  
  
-   他のプロセスで使用できるサービスを作成するテキスト マーカーを使用します。  
  
 コードの領域にテキスト マーカーを適用する方法の詳細については、次を参照してください。[方法: テキスト マーカーを使用して](../extensibility/how-to-use-text-markers.md)します。  
  
## <a name="to-register-a-custom-marker"></a>カスタム マーカーを登録するには  
  
1.  レジストリ エントリを作成します。  
  
     **Hkey_local_machine \software\microsoft\visualstudio\\\<バージョン > \Text Editor\External マーカー\\\<MarkerGUID >**  
  
     *\<MarkerGUID >* は、`GUID`追加される、マーカーを識別するために使用  
  
     `<Version>` バージョンである[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]8.0 などの  
  
     `<PackageGUID>` オートメーション オブジェクトを実装する VSPackage の GUID です。  
  
    > [!NOTE]
    >  ルート パス**\software\microsoft\visualstudio\\\<バージョン >** 詳細詳細については、Visual Studio シェルが初期化されるときに、代替ルートで上書きすることができます[コマンド ライン スイッチ](../extensibility/command-line-switches-visual-studio-sdk.md)します。  
  
2.  次の 4 つの値を作成する**\software\microsoft\visualstudio\\\<バージョン > \Text Editor\External マーカー\\\<MarkerGUID >**  
  
    -   (既定)  
  
    -   サービス  
  
    -   DisplayName  
  
    -   Package  
  
    -   `Default` REG_SZ 型の省略可能なエントリです。 設定すると、エントリの値は、便利な識別情報、たとえば「カスタム テキスト マーカー」を含む文字列です。  
  
    -   `Service` REG_SZ 型のエントリは proffering によってカスタム テキスト マーカーを提供するサービスの GUID の文字列を含む<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider>します。 形式は、{XXXXXX XXXX XXXX XXXX XXXXXXXXX} です。  
  
    -   `DisplayName` カスタム テキスト マーカーの名前のリソース ID を含む REG_SZ 型のエントリです。 形式は、#YYYY です。  
  
    -   `Package` REG_SZ が含まれる型のエントリには、`GUID`のサービスを提供する VSPackage は、サービスの下に一覧表示します。 形式は、{XXXXXX XXXX XXXX XXXX XXXXXXXXX} です。  
  
## <a name="to-create-a-custom-text-marker"></a>カスタム テキスト マーカーを作成するには  
  
1.  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType> インターフェイスを実装します。  
  
     このインターフェイスの実装では、動作と、カスタムのマーカーの種類の外観を定義します。  
  
     このインターフェイスが呼び出されます  
  
    1.  ユーザーは、最初に、IDE を起動します。  
  
    2.  ユーザーが選択、**既定値をリセット**下ボタン、**フォントおよび色**プロパティ ページで、**環境**の左側のウィンドウにある、フォルダー、 **オプション** ダイアログ ボックスがから取得した、**ツール**IDE のメニュー。  
  
2.  実装、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider.GetTextMarkerType%2A>メソッドを指定する`IVsPackageDefinedTextMarkerType`実装する必要がありますに基づいて返されるマーカーの種類のメソッド呼び出しで指定された GUID。  
  
     環境が、カスタムのマーカーの種類が作成され、カスタムのマーカーの種類を識別する GUID を指定します。 このメソッドの最初の時間を呼び出します。  
  
## <a name="to-proffer-your-marker-type-as-a-service"></a>マーカーの種類をサービスとして提供するには  
  
1.  呼び出す、<xref:Microsoft.VisualStudio.OLE.Interop.IOleComponentManager.QueryService%2A>メソッド<xref:Microsoft.VisualStudio.Shell.Interop.SProfferService>します。  
  
     ポインター<xref:Microsoft.VisualStudio.Shell.Interop.IProfferService>が返されます。  
  
2.  呼び出す、 <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.ProfferService%2A> 、カスタム マーカーの種類のサービスを識別しての実装へのポインターを提供する GUID を指定して、メソッド、<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>インターフェイス。 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>実装の実装にポインターを返す必要があります<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider>インターフェイス。  
  
     サービスが返されることを識別する一意の cookie。 呼び出すことによって、カスタム マーカーの種類のサービスを取り消すこの cookie を後で使用することができます、<xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A>のメソッド、<xref:Microsoft.VisualStudio.Shell.Interop.IProfferService>この cookie の値を指定するインターフェイス。  
  
## <a name="see-also"></a>関連項目  
 [テキスト マーカーを使用して、従来の API を使用しました。](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [方法: 標準のテキスト マーカーの追加](../extensibility/how-to-add-standard-text-markers.md)   
 [方法: エラーのマーカーの実装](../extensibility/how-to-implement-error-markers.md)   
 [方法: テキスト マーカーを使用](../extensibility/how-to-use-text-markers.md)