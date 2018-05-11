---
title: IManagedAddin インターフェイス |Microsoft ドキュメント
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- IManagedAddin interface
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d626257d3a2683a6fbb6032e8053572fd1301645
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="imanagedaddin-interface"></a>IManagedAddin インターフェイス
  実装を読み込むコンポーネントを作成する IManagedAddin インターフェイスは、VSTO アドインを管理します。このインターフェイスは、2007 Microsoft Office system に追加された機能です。  
  
## <a name="syntax"></a>構文  
  
```  
[  
    object,  
    uuid(B9CEAB65-331C-4713-8410-DDDAF8EC191A),  
    pointer_default(unique),  
    oleautomation  
]  
interface IManagedAddin : IUnknown  
{  
    HRESULT Load(  
        [in] BSTR bstrManifestURL,   
        [in] IDispatch *pdispApplication);  
    HRESULT Unload();  
};  
```  
  
## <a name="methods"></a>メソッド  
 IManagedAddin インターフェイスによって定義されているメソッドを次の表に示します。  
  
|名前|説明|  
|----------|-----------------|  
|[IManagedAddin::Load](../vsto/imanagedaddin-load.md)|Microsoft Office アプリケーションがマネージ VSTO アドインを読み込むときに呼び出されます。|  
|[IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)|Microsoft Office アプリケーションがマネージ VSTO アドインをアンロードする直前に呼び出されます。|  
  
## <a name="remarks"></a>コメント  
 2007 Microsoft Office system 以降の Microsoft Office アプリケーションの場合は、Office、VSTO アドインの読み込みに IManagedAddin インターフェイスを使用します。独自の VSTO アドイン ローダーを作成する IManagedAddin インターフェイスを実装して、用のランタイム マネージ VSTO アドイン ローダー (VSTOLoader.dll) を使用する代わりに VSTO アドインと[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]です。 詳細については、「 [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)」を参照してください。  
  
## <a name="how-managed-add-ins-are-loaded"></a>マネージ アドイン読み込みのしくみ  
 アプリケーションが起動すると、次の処理が行われます。  
  
1.  アプリケーションによって、次のレジストリ キーにあるエントリが検索され、VSTO アドインが検出されます。  
  
     HKEY_CURRENT_USER\Software\Microsoft\Office\\*\<アプリケーション名 >* \Addins\  
  
     このレジストリ キーにある各エントリは、VSTO アドインの一意な ID です。 通常、これは VSTO アドイン アセンブリの名前です。  
  
2.  アプリケーションによって、各 VSTO アドイン エントリにある `Manifest` エントリが検索されます。  
  
     マネージ VSTO アドインのマニフェストの完全なパスを格納できます、 `Manifest` HKEY_CURRENT_USER\Software\Microsoft\Office エントリ\\*\<アプリケーション名 >* \Addins\\ *\<アドイン ID >* です。 マニフェストは、VSTO アドインの読み込みに使用される情報を提供するファイル (通常は XML ファイル) です。  
  
3.  アプリケーションによって `Manifest` エントリが検出されると、そのアプリケーションはマネージ VSTO アドイン ローダー コンポーネントの読み込みを試みます。 アプリケーションではこの IManagedAddin インターフェイスを実装する COM オブジェクトを作成することによって行われます。  
  
     [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] VSTO アドイン ローダー コンポーネント (VSTOLoader.dll) が含まれています、IManagedAddin インターフェイスを実装してユーザー独自の設定を作成したりできます。  
  
4.  アプリケーションによって [IManagedAddin::Load](../vsto/imanagedaddin-load.md) メソッドが呼び出され、 `Manifest` エントリの値に渡されます。  
  
5.  [IManagedAddin::Load](../vsto/imanagedaddin-load.md) メソッドによって、読み込む VSTO アドイン用のアプリケーション ドメインやセキュリティ ポリシーの構成など、VSTO アドイン読み込みに必要なタスクが実行されます。  
  
 Microsoft Office アプリケーションを検出して読み込むに使用するキーは、VSTO アドインのマネージ レジストリの詳細についてを参照してください[VSTO アドインのレジストリ エントリ](../vsto/registry-entries-for-vsto-add-ins.md)です。  
  
## <a name="guidance-for-implementing-imanagedaddin"></a>IManagedAddin の実装に関するガイダンス  
 IManagedAddin を実装する場合、次の CLSID を使用して実装を含む DLL を登録する必要があります。  
  
 99D651D7-5F7C-470E-8A3B-774D5D9536AC  
  
 Microsoft Office アプリケーションでは、この CLSID を使用して、IManagedAddin を実装する COM オブジェクトを作成します。  
  
> [!CAUTION]  
>  この CLSID は、 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]で VSTOLoader.dll によっても使用されます。 したがって、IManagedAddin を使用して、独自の VSTO アドイン ローダーおよびランタイム コンポーネントを作成することはできませんを配置した場合、コンポーネントに依存している VSTO アドインを実行しているコンピューター、[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]です。  
  
## <a name="see-also"></a>関連項目  
 [アンマネージ API リファレンス&#40;Visual Studio での Office 開発&#41;](../vsto/unmanaged-api-reference-office-development-in-visual-studio.md)  
  
  