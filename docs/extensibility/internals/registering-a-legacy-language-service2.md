---
title: レガシ言語の Service2 の登録 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, language services
- language services, registry information
- registry, language services
ms.assetid: ca312aa3-f9f1-4572-8553-89bf3a724deb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a5d65617a354bc5e752d138bc2cf80261ba2736a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54955156"
---
# <a name="registering-a-legacy-language-service"></a>従来の言語サービスを登録します。
次のセクションでは、オプションを提供レジストリ エントリの一覧のさまざまな言語サービスで使用できる[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]します。  
  
 次のレジストリ エントリの一覧に*VS Reg ルート*は hkey_local_machine \software\microsoft\visualstudio と等しく\\*X.Y*ここで、 *X.Y*が、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]バージョン番号。  
  
## <a name="registry-entries-for-language-service-options"></a>言語サービスのオプションのレジストリ エントリ  
 *VS Reg ルート*\Languages\Language サービス\\*言語名*キーは、次の値を含めることができます。  
  
|名前|型|範囲|説明|  
|----------|----------|-----------|-----------------|  
|(既定)|REG_SZ|*\<GUID>*|言語サービスの GUID です。|  
|LangResID|REG_DWORD|0x0-0 xffff|言語のローカライズされたテキストの名前のリソース識別子 (ResID) の文字列を指定します。|  
|パッケージ|REG_SZ|*\<GUID>*|VSPackage の GUID です。|  
|ShowCompletion|REG_DWORD|0-1|指定するかどうか、**ステートメント入力候補**オプション、**オプション** ダイアログ ボックスが有効にします。|  
|ShowSmartIndent|REG_DWORD|0-1|指定するかどうかを選択するオプション**スマート**でインデント、**オプション** ダイアログ ボックスが有効にします。|  
|RequestStockColors|REG_DWORD|0-1|指定しますカスタムかどうか、またはキーワードに色を既定の色を使用します。|  
|ShowHotURLs|REG_DWORD|0-1|ユーザーが Url をクリックするかどうかを指定します。|  
|既定で非ホット Url|REG_DWORD|0-1|初期設定を指定します、**シングル クリックでの URL ナビゲーションを有効にする**オプション、**オプション** ダイアログ ボックス。|  
|DefaultToInsertSpaces|REG_DWORD|0-1|言語サービスがその既定値 タブのオプションとして「スペースを挿入する」を使用するかどうかを指定します。|  
|ShowDropdownBarOption|REG_DWORD|0-1|有効または無効に、**ナビゲーション バー**オプション、**オプション**ダイアログ ボックスを表示または非表示、**ナビゲーション バー**します。|  
|1 つのコードのみ ウィンドウ|REG_DWORD|0-1|有効または無効に、**新しいウィンドウ**の選択肢、**ウィンドウ**言語サービスのメニュー。|  
|EnableAdvancedMembersOption|REG_DWORD|0-1|有効または無効にする**オプション**のダイアログ ボックスの設定**メンバーの詳細を非表示にする**。|  
|CF_HTML のサポート|REG_DWORD|0-1|HTML データのコピー アンド ペースト エディターが有効かどうかを指定します。|  
|EnableLineNumbersOption|REG_DWORD|0-1|指定するかどうか、**行番号**オプション、**オプション**言語サービスのダイアログ ボックスが有効になっています。|  
|HideAdvancedMembersByDefault|REG_DWORD|0-1|プライベート フィールドなどの高度なメンバーが入力候補一覧に非表示かどうかを指定します。|  
|ShowBraceCompletion|REG_DWORD|0-1|指定するかどうか、**かっこの補完**オプション、**オプション** ダイアログ ボックスが有効にします。|  
  
### <a name="example"></a>例  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    Language Services\  
      C/C++\  
        (Default)             = reg_sz:{B2F072B0-ABC1-11D0-9D62-00C04FD9DFD9}  
        LangResID             = reg_dword:0x00000000  
        Package               = reg_sz:{8C2EA640-ABC1-11D0-9D62-00C04FD9DFD9}  
        ShowCompletion        = reg_dword:0x00000001  
        ShowSmartIndent       = reg_dword:0x00000001  
        ShowDropdownBarOption = reg_dword:0x00000001  
```  
  
## <a name="registry-entries-for-debugger-languages-options"></a>デバッガーの言語のオプションのレジストリ エントリ  
 *VS Reg ルート*\Languages\Language サービス\\*言語名*\Debugger 言語\\*GUID*\ キーは、次を含めることができます値。  
  
|名前|型|範囲|説明|  
|----------|----------|-----------|-----------------|  
|(既定)|REG_SZ|テキスト|既定値は、ドキュメントの言語の名前を使用できます。 このキーの名前は GUID に対応するエントリを含む式エバリュエーターの *\<VS Reg ルート >* \AD7Metrics\Expression エバリュエーター。|  
  
### <a name="example"></a>例  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    Language Services\  
      C/C++\  
        Debugger Languages\  
          {3A12D0B7-C26C-11D0-B442-00A0244A1DD2}\  
            (Default) = reg_sz:C++  
```  
  
## <a name="registry-entries-for-editor-tools-options"></a>エディターのツール オプションのレジストリ エントリ  
 プロパティ ページおよびプロパティ ノード EditorToolsOptions キーの下のレジストリ キーを追加することができます。 これらのキーとその値の特定のプロパティ ページ、**オプション** ダイアログ ボックス (上、**ツール**メニュー)、言語サービスの構成に使用します。 次の例では、*ページ名*プロパティ ページでの名前を指定し、*ノード名*で、ツリー内のノードの名前は、**オプション** ダイアログ ボックス。 ページのエントリとノード エントリを個別に指定する必要があります。  
  
|名前|型|範囲|説明|  
|----------|----------|-----------|-----------------|  
|(既定)|REG_SZ|resID|このオプション ページのローカライズされた表示名。 名前はリテラル テキスト、または # できます`nnn`ここで、`nnn`はサテライト DLL を指定した VSPackage の文字列リソース ID です。|  
|パッケージ|REG_SZ|*GUID*|このオプション ページを実装する VSPackage の GUID です。|  
|ページ|REG_SZ|*GUID*|呼び出すことによって、VSPackage から要求するプロパティ ページの GUID、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>メソッド。 このレジストリ エントリが存在しない場合、レジストリ キーは、ページではなく、ノードを示します。|  
  
### <a name="example"></a>例  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    Language Services\  
      CSharp\  
        EditorToolsOptions\  
          Formatting\  
            (Default) = reg_sz:#242  
            Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}  
            General\  
              (Default) = reg_sz:#255  
              Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}  
              Page      = reg_sz:{3EB2CC0B-033E-4D75-B26A-B2362C25227E}  
            Indentation\  
              (Default) = reg_sz:#250  
              Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}  
              Page      = reg_sz:{5E21D017-6D2A-4114-A1F1-C923F001CBBB}  
            Newlines\  
              (Default) = reg_sz:#253  
              Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}  
              Page      = reg_sz:{607D8062-68D1-41E4-9A35-B5E7F14D0481}  
```  
  
## <a name="registry-entries-for-file-name-extension-options"></a>ファイル名拡張子のオプションのレジストリ エントリ  
 ファイル拡張子のエントリには、".myext"など、先行するピリオドを含める必要があります。  
  
|名前|型|範囲|説明|  
|----------|----------|-----------|-----------------|  
|(既定)|REG_SZ|*GUID*|このファイル名拡張子の種類の既定の言語サービスのサービスの GUID です。|  
  
### <a name="example"></a>例  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    File Extensions\  
      .cpp\  
        (Default) = {B2F072B0-ABC1-11D0-9D62-00C04FD9DFD9}  
```  
  
## <a name="registry-entries-for-editor-options"></a>エディターのオプションのレジストリ エントリ  
 *VS Reg ルート*\Editors キーは、次の値を含めることができます。  
  
|名前|型|範囲|説明|  
|----------|----------|-----------|-----------------|  
|(既定)|REG_SZ|""|使用されていません。ドキュメントについては、名はここに配置できます。|  
|DefaultToolboxTab|REG_SZ|""|エディターがアクティブな場合は既定値に、[ツールボックス] タブの名前です。|  
|DisplayName|REG_SZ|resID|表示される名前、**プログラムから開く** ダイアログ ボックス。 名前は、標準形式で文字列リソース ID または名前。|  
|ExcludeDefTextEditor|REG_DWORD|0-1|使用、**プログラムから開く**メニュー コマンド。 特定のファイルの種類に対して使用可能なエディターの一覧で、既定のテキスト エディターを一覧表示したくない場合は、この値を 1 に設定します。|  
|LinkedEditorGUID|REG_SZ|*\<GUID>*|コード ページのサポート ファイルを開くことができる任意の言語サービスに使用されます。 たとえば、ファイルを開くと、.txt を使用して、**ファイルを開く**コマンド、オプションが、エンコードなしでは、ソース コード エディターを使用するために用意されています。 します。<br /><br /> サブキーの名前を指定の GUID がコード ページ エディター ファクトリです。この特定のレジストリ エントリで指定されたリンクの GUID は、正規表現エディター ファクトリです。 このエントリの目的は、IDE で、既定のエディターを使用して、ファイルが表示されない場合、IDE は、一覧で、[次へ] エディターを使用してください。 このエディターのファクトリは基本的に失敗したエディター ファクトリと同じであるために、この次のエディターはコード ページ エディターのファクトリをしないでください。|  
|パッケージ|REG_SZ|*\<GUID>*|表示名の ResID の VSPackage の GUID です。|  
  
### <a name="example"></a>例  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  \Editors\  
    {8281C572-2171-45AA-A642-7D8BC1662F1C}\  
      (Default)            = reg_sz:Html Editor with Encoding  
      DefaultToolboxTab    = reg_sz:HTML  
      DisplayName          = reg_sz:#20101  
      LinkedEditorGUID     = reg_sz:{C76D83F8-A489-11D0-8195-00A0C91BBEE3}  
      Package              = reg_sz:{1B437D20-F8FE-11D2-A6AE-00104BCC7269}  
```  
  
## <a name="registry-entries-for-logical-view-options"></a>論理ビューのオプションのレジストリ エントリ  
 *VS Reg ルート*\Editors\\*エディター GUI >* \LogicalViews キーは、次の値を含めることができます。  
  
|名前|型|範囲|説明|  
|----------|----------|-----------|-----------------|  
|(既定)|REG_SZ||使用されません。|  
|*\<GUID>*|REG_SZ|""|サポートされる論理ビューへのキー。 必要に応じて、これらの多くができます。 レジストリ エントリの名前は、重要な値ではなく、空の文字列では常にします。|  
  
### <a name="example"></a>例  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  \Editors\  
    {8281C572-2171-45AA-A642-7D8BC1662F1C}\  
      LogicalViews\  
       (Default) = reg_sz:  
       {7651a700-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:  
       {7651a701-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:  
       {7651a702-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:  
       {7651a703-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:  
```  
  
## <a name="registry-entries-for-editor-extension-options"></a>エディター拡張機能のオプションのレジストリ エントリ  
 *VS Reg ルート*\Editors\\*エディター GUID*\Extensions キーは、次の値を含めることができます。 ファイル名拡張子では、先行するピリオドが含まれません。  
  
|名前|型|範囲|説明|  
|----------|----------|-----------|-----------------|  
|(既定)|REG_SZ||使用されません。|  
|*\<ext>*|REG_DWORD|0-0 xffffffff|拡張機能の相対的な優先順位。 2 つまたは複数の言語では、同じ拡張機能を共有する場合は、優先順位の高い言語が選択されます。|  
  
 さらに、エディターの現在のユーザーの既定の選択は hkey_current_user \software\microsoft\visualstudio\\*X.Y*\Default エディター\\*ext*します。選択した言語サービスの GUID は、カスタム エントリでです。 これは、現在のユーザーの優先します。  
  
### <a name="example"></a>例  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0\  
  \Editors\  
    {8281C572-2171-45AA-A642-7D8BC1662F1C}\  
      Extensions\  
       (Default) = reg_sz:  
       *         = reg_dword:0x00000018  
       html      = reg_dword:0x00000027  
       shtm      = reg_dword:0x00000027  
       shtml     = reg_dword:0x00000027  
```  
  
## <a name="registry-entries-for-managed-package-framework-language-service-options"></a>Managed Package Framework の言語サービスのオプションのレジストリ エントリ  
 次のレジストリ エントリは、マネージ パッケージ フレームワーク (MPF) の言語サービス クラスに固有です。 これらのレジストリ エントリは、IntelliSense のさまざまな機能とその他の編集機能の詳細の言語サービスでサポートを示します。  
  
 これらのレジストリ エントリを使用してアクセスされる、<xref:Microsoft.VisualStudio.Package.LanguagePreferences>クラス。  
  
|名前|型|範囲|説明|  
|----------|----------|-----------|-----------------|  
|CodeSense|REG_DWORD|0-1|IntelliSense の操作をサポートします。|  
|MatchBraces|REG_DWORD|0-1|一致する中かっこ、かっこ、角かっこなどの言語のペアをサポートします。|  
|QuickInfo|REG_DWORD|0-1|IntelliSense によるクイック ヒントの操作をサポートします。|  
|ShowMatchingBrace|REG_DWORD|0-1|ステータス バーに一致する言語のペアを表示するためのサポート。|  
|MatchBracesAtCaret|REG_DWORD|0-1|通常、2 つの要素を強調表示を一致する言語の組み合わせを表示するためのサポート。|  
|MaxErrorMessages|REG_DWORD|0 ~ n|表示できるエラーの最大数、**エラー一覧**ウィンドウ。|  
|CodeSenseDelay|REG_DWORD|0 ~ n|任意のバック グラウンド解析 IntelliSense の操作を開始する前に遅延するミリ秒数。|  
|EnableAsyncCompletion|REG_DWORD|0-1|バック グラウンドの解析をサポートします。|  
|EnableCommenting|REG_DWORD|0-1|選択した、テキスト ブロックをコメント アウトのサポートし、選択したテキストをコメント解除のサポートを意味しています。|  
|EnableFormatSelection|REG_DWORD|0-1|自動インデントなどのテキストの書式設定、または中かっこの位置を調整することをサポートします。|  
|AutoOutlining|REG_DWORD|0-1|アウトライン (縮小可能な領域) をサポートします。|  
|MaxRegions|REG_DWORD|0 ~ n|ファイルあたりの非表示の領域の最大数。|  
  
```  
ExampleHKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    Language Services\  
      XML\  
        (Default)             = reg_sz:{f6819a78-a205-47b5-be1c-675b3c7f0b8e}  
        MatchBraces           = reg_dword:0x00000001  
        QuickInfo             = reg_dword:0x00000001  
        ShowMatchingBrace     = reg_dword:0x00000001  
        MatchBracesAtCaret    = reg_dword:0x00000000  
        MaxErrorMessages      = reg_dword:0x00000064  
        CodeSenseDelay        = reg_dword:0x000001f4  
        MaxRegions            = reg_dword:0x0000000a  
```  
  
## <a name="see-also"></a>関連項目  
 [従来の言語サービスの開発](../../extensibility/internals/developing-a-legacy-language-service.md)