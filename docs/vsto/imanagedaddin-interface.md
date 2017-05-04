---
title: "IManagedAddin インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "IManagedAddin インターフェイス"
ms.assetid: 5350629c-6cf8-42dd-ae65-3f34322ee10f
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# IManagedAddin インターフェイス
  IManagedAddin インターフェイスを実装すると、マネージ VSTO アドインを読み込むコンポーネントを作成できます。 このインターフェイスは、2007 Microsoft Office system に追加された機能です。  
  
## 構文  
  
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
  
## メソッド  
 IManagedAddin インターフェイスで定義されているメソッドを次の表に示します。  
  
|名前|説明|  
|--------|--------|  
|[IManagedAddin::Load](../vsto/imanagedaddin-load.md)|Microsoft Office アプリケーションがマネージ VSTO アドインを読み込むときに呼び出されます。|  
|[IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)|Microsoft Office アプリケーションがマネージ VSTO アドインをアンロードする直前に呼び出されます。|  
  
## 解説  
 2007 Microsoft Office system 以降の Microsoft Office アプリケーションでは、Office VSTO アドインを読み込むのに IManagedAddin インターフェイスが使用されるようになりました。IManagedAddin インターフェイスを実装すると、VSTO アドイン ローダー \(VSTOLoader.dll\) や [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] を使用する代わりに、ユーザー独自の VSTO アドイン ローダーやマネージ VSTO アドイン用のランタイムを作成できます。 詳細については、「[VSTO アドインのアーキテクチャ](../vsto/architecture-of-vsto-add-ins.md)」を参照してください。  
  
## マネージ アドイン読み込みのしくみ  
 アプリケーションが起動すると、次の処理が行われます。  
  
1.  アプリケーションによって、次のレジストリ キーにあるエントリが検索され、VSTO アドインが検出されます。  
  
     HKEY\_CURRENT\_USER\\Software\\Microsoft\\Office\\*\<application name\>*\\Addins\\  
  
     このレジストリ キーにある各エントリは、VSTO アドインの一意な ID です。 通常、これは VSTO アドイン アセンブリの名前です。  
  
2.  アプリケーションによって、各 VSTO アドイン エントリにある `Manifest` エントリが検索されます。  
  
     マネージ VSTO アドインは、HKEY\_CURRENT\_USER\\Software\\Microsoft\\Office\\*\<application name\>*\\Addins\\*\<add\-in ID\>* にある `Manifest` エントリに、マニフェストの完全パスを格納できます。 マニフェストは、VSTO アドインの読み込みに使用される情報を提供するファイル \(通常は XML ファイル\) です。  
  
3.  アプリケーションによって `Manifest` エントリが検出されると、そのアプリケーションはマネージ VSTO アドイン ローダー コンポーネントの読み込みを試みます。 このアプリケーションによる読み込みは、IManagedAddin インターフェイスを実装する COM オブジェクトを作成することで行われます。  
  
     [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] には、VSTO アドイン ローダー コンポーネント \(VSTOLoader.dll\) が含まれていますが、IManagedAddin インターフェイスを実装してユーザー独自のアドイン ローダーを作成することもできます。  
  
4.  アプリケーションによって [IManagedAddin::Load](../vsto/imanagedaddin-load.md) メソッドが呼び出され、`Manifest` エントリの値に渡されます。  
  
5.  [IManagedAddin::Load](../vsto/imanagedaddin-load.md) メソッドによって、読み込む VSTO アドイン用のアプリケーション ドメインやセキュリティ ポリシーの構成など、VSTO アドイン読み込みに必要なタスクが実行されます。  
  
 Microsoft Office アプリケーションがマネージ VSTO アドインの検出と読み込みに使用するレジストリ キーについて詳しくは、「[VSTO アドインのレジストリ エントリ](../vsto/registry-entries-for-vsto-add-ins.md)」をご覧ください。  
  
## IManagedAddin の実装に関するガイダンス  
 IManagedAddin を実装する場合には、次の CLSID を使用して実装のある DLL を登録する必要があります。  
  
 99D651D7\-5F7C\-470E\-8A3B\-774D5D9536AC  
  
 Microsoft Office アプリケーションは、この CLSID を使用して IManagedAddin を実装する COM オブジェクトを作成します。  
  
> [!CAUTION]  
>  この CLSID は、[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] で VSTOLoader.dll によっても使用されます。 したがって、ユーザー独自の VSTO アドイン ローダーおよびランタイム コンポーネントを作成するために IManagedAddin を使用した場合、これらのコンポーネントは [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] を使用して VSTO アドインを実行しているコンピューターには配置できません。  
  
## 参照  
 [アンマネージ API リファレンス &#40;Visual Studio での Office 開発&#41;](../vsto/unmanaged-api-reference-office-development-in-visual-studio.md)  
  
  