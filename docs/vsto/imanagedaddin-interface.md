---
title: IManagedAddin インターフェイス
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
ms.openlocfilehash: b113d0d62156d77d08fa2fcdbb415d0518eba3a8
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2018
ms.locfileid: "35671898"
---
# <a name="imanagedaddin-interface"></a>IManagedAddin インターフェイス
  読み込むコンポーネントを作成するには、その IManagedAddin インターフェイスを実装では、VSTO アドインを管理します。このインターフェイスは、2007 Microsoft Office system に追加された機能です。  
  
## <a name="syntax"></a>構文  
  
```csharp
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
|[IManagedAddin::Load](../vsto/imanagedaddin-load.md)|Microsoft Office アプリケーションがマネージド VSTO アドインを読み込むときに呼び出されます。|  
|[IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)|Microsoft Office アプリケーションがマネージド VSTO アドインをアンロードする直前に呼び出されます。|  
  
## <a name="remarks"></a>Remarks  
 以降、2007 Microsoft Office system では、Microsoft Office アプリケーションでは、Office VSTO アドインの読み込みに IManagedAddin インターフェイスを使用します。独自の VSTO アドイン ローダーを作成する IManagedAddin インターフェイスを実装して、ランタイムをマネージ VSTO アドイン ローダーを使用する代わりに VSTO アドイン (*VSTOLoader.dll*) と[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]します。 詳細については、「 [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)」を参照してください。  
  
## <a name="how-managed-add-ins-are-loaded"></a>マネージ アドインを読み込む方法  
 アプリケーションが起動すると、次の処理が行われます。  
  
1.  アプリケーションによって、次のレジストリ キーにあるエントリが検索され、VSTO アドインが検出されます。  
  
     **HKEY_CURRENT_USER\Software\Microsoft\Office\\_\<アプリケーション名 >_ \Addins\**  
  
     このレジストリ キーにある各エントリは、VSTO アドインの一意な ID です。 通常、これは VSTO アドイン アセンブリの名前です。  
  
2.  アプリケーションによって、各 VSTO アドイン エントリにある `Manifest` エントリが検索されます。  
  
     マネージ VSTO アドインのマニフェストの完全なパスを格納できる、`Manifest`エントリ**HKEY_CURRENT_USER\Software\Microsoft\Office\\_\<アプリケーション名 >_ \Addins\\_\<アドイン ID >_** します。 マニフェストは、VSTO アドインの読み込みに使用される情報を提供するファイル (通常は XML ファイル) です。  
  
3.  アプリケーションによって `Manifest` エントリが検出されると、そのアプリケーションはマネージド VSTO アドイン ローダー コンポーネントの読み込みを試みます。 アプリケーションは、IManagedAddin インターフェイスを実装する COM オブジェクトを作成しようとしています。  
  
     [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] VSTO アドイン ローダー コンポーネントが含まれています (*VSTOLoader.dll*)、または IManagedAddin インターフェイスを実装して、独自に作成することができます。  
  
4.  アプリケーションによって [IManagedAddin::Load](../vsto/imanagedaddin-load.md) メソッドが呼び出され、 `Manifest` エントリの値に渡されます。  
  
5.  [IManagedAddin::Load](../vsto/imanagedaddin-load.md) メソッドによって、読み込む VSTO アドイン用のアプリケーション ドメインやセキュリティ ポリシーの構成など、VSTO アドイン読み込みに必要なタスクが実行されます。  
  
 Microsoft Office アプリケーションを検出して読み込むに使用するキーが VSTO アドインを管理対象レジストリの詳細についてを参照してください[VSTO アドインのレジストリ エントリ](../vsto/registry-entries-for-vsto-add-ins.md)します。  
  
## <a name="guidance-to-implement-imanagedaddin"></a>IManagedAddin を実装するためのガイダンス  
 IManagedAddin を実装する場合は、次の CLSID を使用して実装を含んでいる DLL を登録する必要があります。  
  
 99D651D7-5F7C-470E-8A3B-774D5D9536AC  
  
 Microsoft Office アプリケーションでは、この CLSID を使用して、読み込みを実装する COM オブジェクトを作成します。  
  
> [!CAUTION]  
>  この CLSID はによっても使用*VSTOLoader.dll*で、[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]します。 そのため、IManagedAddin を使用して、独自の VSTO アドイン ローダーおよびランタイム コンポーネントを作成する場合は展開できませんコンポーネントに依存する VSTO アドインを実行しているコンピューターに、[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]します。  
  
## <a name="see-also"></a>関連項目  
 [アンマネージ API リファレンス&#40;Visual Studio での Office 開発&#41;](../vsto/unmanaged-api-reference-office-development-in-visual-studio.md)  
  
  