---
title: '方法: カスタム テキスト マーカーの作成 |Microsoft Docs'
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
- editors [Visual Studio SDK], legacy - custom text markers
ms.assetid: 6e32ed81-c604-4a32-9012-8db3bec7c846
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3b0a280b44ad468ba44baf81efcc4e4569638e8b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51783091"
---
# <a name="how-to-create-custom-text-markers"></a>方法: カスタム テキスト マーカーの作成
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

強調したり、コードを整理するカスタム テキスト マーカーを作成する場合は、以下の手順を実行する必要があります。  
  
- その他のツールがアクセスできるように、新しいテキスト マーカーを登録します。  
  
- 既定の実装とテキスト マーカーの構成を指定します。  
  
- 他のプロセスで使用できるサービスを作成するテキスト マーカーの使用  
  
  コードの領域にテキスト マーカーを適用する方法の詳細については、次を参照してください。[方法: テキスト マーカーを使用して](../extensibility/how-to-use-text-markers.md)します。  
  
### <a name="to-register-a-custom-marker"></a>カスタム マーカーを登録するには  
  
1. レジストリ エントリを作成します。  
  
    Hkey_local_machine \software\microsoft\visualstudio\\*\<バージョン >* \Text Editor\External マーカー\\*\<MarkerGUID >*  
  
    <em>\<MarkerGUID ></em>は、`GUID`追加される、マーカーを識別するために使用  
  
    *\<バージョン >* のバージョンである[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]8.0 などの  
  
    *\<PackageGUID >* オートメーション オブジェクトを実装する VSPackage の GUID です。  
  
   > [!NOTE]
   >  Hkey_local_machine \software\microsoft\visualstudio のルート パス\\*\<バージョン >* 詳細詳細については、Visual Studio シェルが初期化されるときに、代替ルートで上書きすることができます[コマンド ライン スイッチ](../extensibility/command-line-switches-visual-studio-sdk.md)します。  
  
2. Hkey_local_machine \software\microsoft\visualstudio で 4 つの値を作成する\\*\<バージョン >* \Text Editor\External マーカー\\*\<MarkerGUID>*  
  
   -   (既定)  
  
   -   サービス  
  
   -   DisplayName  
  
   -   Package  
  
   -   `Default` REG_SZ 型の省略可能なエントリです。 設定すると、エントリの値は、便利な識別情報、たとえば「カスタム テキスト マーカー」を含む文字列です。  
  
   -   `Service` REG_SZ 型のエントリは proffering によってカスタム テキスト マーカーを提供するサービスの GUID の文字列を含む<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider>します。 形式は、{XXXXXX XXXX XXXX XXXX XXXXXXXXX} です。  
  
   -   `DisplayName` カスタム テキスト マーカーの名前のリソース ID を含む REG_SZ 型のエントリです。 形式は、#YYYY です。  
  
   -   `Package` REG_SZ が含まれる型のエントリには、`GUID`のサービスを提供する VSPackage は、サービスの下に一覧表示します。 形式は、{XXXXXX XXXX XXXX XXXX XXXXXXXXX} です。  
  
### <a name="to-create-a-custom-text-marker"></a>カスタム テキスト マーカーを作成するには  
  
1.  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType> インターフェイスを実装します。  
  
     このインターフェイスの実装では、動作と、カスタムのマーカーの種類の外観を定義します。  
  
     このインターフェイスが呼び出されます  
  
    1.  ユーザーは、最初に、IDE を起動します。  
  
    2.  ユーザーが選択、**既定値をリセット**下ボタン、**フォントおよび色**プロパティ ページで、**環境**の左側のウィンドウにある、フォルダー、 **オプション** ダイアログ ボックスがから取得した、**ツール**IDE のメニュー。  
  
2.  実装、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider.GetTextMarkerType%2A>メソッドを指定する`IVsPackageDefinedTextMarkerType`実装する必要がありますに基づいて返されるマーカーの種類のメソッド呼び出しで指定された GUID。  
  
     環境が、カスタムのマーカーの種類が作成され、カスタムのマーカーの種類を識別する GUID を指定します。 このメソッドの最初の時間を呼び出します。  
  
### <a name="to-proffer-your-marker-type-as-a-service"></a>マーカーの種類をサービスとして提供するには  
  
1.  呼び出す、<xref:Microsoft.VisualStudio.OLE.Interop.IOleComponentManager.QueryService%2A>メソッド<xref:Microsoft.VisualStudio.Shell.Interop.SProfferService>します。  
  
     ポインター<xref:Microsoft.VisualStudio.Shell.Interop.IProfferService>が返されます。  
  
2.  呼び出す、 <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.ProfferService%2A> 、カスタム マーカーの種類のサービスを識別しての実装へのポインターを提供する GUID を指定して、メソッド、<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>インターフェイス。 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>実装の実装にポインターを返す必要があります<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider>インターフェイス。  
  
     サービスが返されることを識別する一意の cookie。 呼び出すことによって、カスタム マーカーの種類のサービスを取り消すこの cookie を後で使用することができます、<xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A>のメソッド、<xref:Microsoft.VisualStudio.Shell.Interop.IProfferService>この cookie の値を指定するインターフェイス。  
  
## <a name="see-also"></a>関連項目  
 [レガシ API を使用したテキスト マーカーの使用](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [方法: 標準のテキスト マーカーの追加](../extensibility/how-to-add-standard-text-markers.md)   
 [方法: エラーのマーカーの実装](../extensibility/how-to-implement-error-markers.md)   
 [方法: テキスト マーカーを使用する](../extensibility/how-to-use-text-markers.md)

