---
title: "レガシ言語 Service2 の登録 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "登録には、言語サービス"
  - "言語サービス、レジストリ情報"
  - "レジストリ、言語サービス"
ms.assetid: ca312aa3-f9f1-4572-8553-89bf3a724deb
caps.latest.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 24
---
# 従来の言語サービスを登録します。
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

次のセクションでは、レジストリ エントリのリスト、さまざまな言語で使用できるサービス オプション [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]します。  
  
 次のレジストリ エントリの一覧で *VS Reg ルート* HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\ と等しい*X.Y*, ここで、 *X.Y* は、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] バージョン番号。  
  
## 言語サービスのオプションのレジストリ エントリ  
 *VS Reg ルート*\\Languages\\Language Services\\*言語名* キーは、次の値を含めることができます。  
  
|名前|型|範囲|説明|  
|--------|-------|--------|--------|  
|\(既定\)|REG\_SZ|*\< GUID \>*|言語サービスの GUID です。|  
|LangResID|REG\_DWORD|0x0\-0 xffff|言語のローカライズされたテキストの名前のリソース識別子 \(ResID\) の文字列を指定します。|  
|パッケージ|REG\_SZ|*\< GUID \>*|VSPackage の GUID です。|  
|ShowCompletion|REG\_DWORD|0\-1|指定するかどうか、 **ステートメント入力候補** オプションには、 **オプション** \] ダイアログ ボックスがオンになっています。|  
|ShowSmartIndent|REG\_DWORD|0\-1|指定するかどうかを選択するオプション **スマート** でインデント、 **オプション** \] ダイアログ ボックスがオンになっています。|  
|RequestStockColors|REG\_DWORD|0\-1|指定カスタムかどうか、またはキーワードに色を既定の色を使用します。|  
|ShowHotURLs|REG\_DWORD|0\-1|Url にユーザーがクリックするかどうかを指定します。|  
|既定で非ホット Url|REG\_DWORD|0\-1|初期設定を指定、 **シングル クリックでの URL ナビゲーションを有効にする** オプション、 **オプション** \] ダイアログ ボックス。|  
|DefaultToInsertSpaces|REG\_DWORD|0\-1|言語サービスがその既定値\] タブのオプションとして「スペースを挿入する」を使用するかどうかを指定します。|  
|ShowDropdownBarOption|REG\_DWORD|0\-1|有効または無効に、 **ナビゲーション バー** オプション、 **オプション** ダイアログ ボックスを表示または非表示、 **ナビゲーション バー**します。|  
|1 つのコードのみ\] ウィンドウ|REG\_DWORD|0\-1|有効または無効にします **新しいウィンドウ** の選択肢、 **ウィンドウ** 言語サービスのメニュー。|  
|EnableAdvancedMembersOption|REG\_DWORD|0\-1|有効または無効にする **オプション** のダイアログ ボックスの設定 **メンバーの詳細を非表示に**します。|  
|CF\_HTML のサポート|REG\_DWORD|0\-1|HTML のデータをコピーして貼り付けるに、エディターを使用するかどうかを指定します。|  
|EnableLineNumbersOption|REG\_DWORD|0\-1|指定するかどうか、 **行番号** オプションには、 **オプション** 言語サービスのダイアログ ボックスが有効にします。|  
|HideAdvancedMembersByDefault|REG\_DWORD|0\-1|入力候補のリストでのプライベート フィールドなどの高度なメンバーを非表示かどうかを指定します。|  
|ShowBraceCompletion|REG\_DWORD|0\-1|指定するかどうか、 **完了に左中かっこ** オプションに、 **オプション** \] ダイアログ ボックスが有効になっています。|  
  
### 例  
  
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
  
## デバッガーの言語のオプションのレジストリ エントリ  
 *VS Reg ルート*\\Languages\\Language Services\\*言語名*\\Debugger Languages\\*GUID*\\ キーは、次の値を含めることができます。  
  
|名前|型|範囲|説明|  
|--------|-------|--------|--------|  
|\(既定\)|REG\_SZ|テキスト|既定値は、言語の名前を文書化に使用できます。 このキーの名前は、対応するエントリが、式エバリュエーターの GUID *\< VS Reg ルート \>*\\AD7Metrics\\Expression エバリュエーター。|  
  
### 例  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    Language Services\  
      C/C++\  
        Debugger Languages\  
          {3A12D0B7-C26C-11D0-B442-00A0244A1DD2}\  
            (Default) = reg_sz:C++  
```  
  
## エディター オプションのレジストリ エントリ  
 プロパティ ページとプロパティの各ノードの EditorToolsOptions キーの下のレジストリ キーを追加することができます。 これらのキーとその値のプロパティ ページを識別、 **オプション** \] ダイアログ ボックス \(上、 **ツール** メニュー\) 言語サービスの構成に使用されています。 次の例で *ページ名* プロパティ ページの名前を指定し、 *ノード名* にツリー内のノードの名前は、 **オプション** \] ダイアログ ボックス。 ページのエントリがあり、ノードのエントリは、個別に指定する必要があります。  
  
|名前|型|範囲|説明|  
|--------|-------|--------|--------|  
|\(既定\)|REG\_SZ|ResID|このオプション ページのローカライズされた表示名。 名前は、リテラル テキストは、か \# を使用できます`nnn`, ここで、 `nnn` サテライト DLL の指定した VSPackage に文字列リソース id を指定します。|  
|パッケージ|REG\_SZ|*GUID*|このオプション ページを実装する VSPackage の GUID です。|  
|ページ|REG\_SZ|*GUID*|プロパティ ページの GUID を呼び出すことによって、VSPackage から要求を <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> メソッドです。 このレジストリ エントリが存在しない場合、レジストリ キーは、ページではなく、ノードを示します。|  
  
### 例  
  
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
  
## ファイル名拡張子のオプションのレジストリ エントリ  
 ファイル拡張子のエントリは、先行するピリオドをたとえば".myext"を含める必要があります。  
  
|名前|型|範囲|説明|  
|--------|-------|--------|--------|  
|\(既定\)|REG\_SZ|*GUID*|この種類のファイル名拡張子の既定の言語サービスのサービスの GUID です。|  
  
### 例  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    File Extensions\  
      .cpp\  
        (Default) = {B2F072B0-ABC1-11D0-9D62-00C04FD9DFD9}  
```  
  
## エディターのオプションのレジストリ エントリ  
 *VS Reg ルート*\\Editors キーは、次の値を含めることができます。  
  
|名前|型|範囲|説明|  
|--------|-------|--------|--------|  
|\(既定\)|REG\_SZ|""|使用されていません。ドキュメントの名前を配置することができます。|  
|DefaultToolboxTab|REG\_SZ|""|エディターがアクティブな場合は、既定値に \[ツールボックス\] タブの名前です。|  
|DisplayName|REG\_SZ|ResID|表示される名前、 **ファイルを開く** \] ダイアログ ボックス。 名前は、文字列リソース ID または名前標準的な形式です。|  
|ExcludeDefTextEditor|REG\_DWORD|0\-1|使用、 **ファイルを開く** メニュー コマンドです。 使用できるエディターの特定のファイルの種類の一覧で、既定のテキスト エディターを一覧表示したくない場合は、この値を 1 に設定します。|  
|LinkedEditorGUID|REG\_SZ|*\< GUID \>*|コード ページのサポート ファイルを開くことができる言語サービスで使用します。 たとえば、ファイルを開くと、.txt を使用して、 **ファイルを開く** コマンド、およびエンコードせずにソース コード エディターを使用するためのオプションが提供されます。<br /><br /> サブキーの名前を指定する GUID はコード ページ エディター ファクトリです。この特定のレジストリ エントリに指定したリンクされた GUID では、正規エディター ファクトリのです。 このエントリの目的では、IDE で、既定のエディターを使用して、ファイルが表示されない場合は、IDE は、一覧の次のエディターを使用する試みますです。 このエディター ファクトリには基本的には、失敗したエディター ファクトリと同じために、この次のエディターはコードページ エディター ファクトリをしないでください。|  
|パッケージ|REG\_SZ|*\< GUID \>*|表示名の ResID の VSPackage guid を指定します。|  
  
### 例  
  
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
  
## 論理ビューのオプションのレジストリ エントリ  
 *VS Reg ルート*\\Editors\\*エディター GUI \>*\\LogicalViews キーは、次の値を含めることができます。  
  
|名前|型|範囲|説明|  
|--------|-------|--------|--------|  
|\(既定\)|REG\_SZ||使用されていません。|  
|*\< GUID \>*|REG\_SZ|""|サポートされる論理ビューへのキー。 必要に応じて多くのことができます。 レジストリ エントリの名前は、重要な値ではなく、空の文字列では常にします。|  
  
### 例  
  
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
  
## エディター拡張機能のオプションのレジストリ エントリ  
 *VS Reg ルート*\\Editors\\*エディター GUID*\\Extensions キーは、次の値を含めることができます。 ファイル名拡張子では、先行するピリオドは含まれません。  
  
|名前|型|範囲|説明|  
|--------|-------|--------|--------|  
|\(既定\)|REG\_SZ||使用されていません。|  
|*\< テキスト \>*|REG\_DWORD|0 xffffffff に設定|拡張機能の相対的な優先順位。 2 つまたは複数の言語では、同じ拡張機能を共有する場合は、優先度が高い言語が選択されます。|  
  
 さらに、エディターの現在のユーザーの既定の選択は HKEY\_Current\_User\\Software\\Microsoft\\VisualStudio\\*X.Y*\\Default Editors\\*ext*します。 選択した言語サービスの GUID は、カスタム エントリでです。 現在のユーザーの優先順位が表示されます。  
  
### 例  
  
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
  
## マネージ パッケージ フレームワーク言語サービス オプションのレジストリ エントリ  
 次のレジストリ エントリは、マネージ パッケージ フレームワーク \(MPF\) 言語のサービス クラスに固有です。 これらのレジストリ エントリは、さまざまな IntelliSense 機能およびその他の編集機能の詳細の言語サービスでのサポートを示します。  
  
 これらのレジストリ エントリを使用してアクセスされる、 <xref:Microsoft.VisualStudio.Package.LanguagePreferences> クラスです。  
  
|名前|型|範囲|説明|  
|--------|-------|--------|--------|  
|CodeSense|REG\_DWORD|0\-1|IntelliSense の操作をサポートします。|  
|MatchBraces|REG\_DWORD|0\-1|一致する中かっこ、かっこ、および角かっこなどの言語ペアをサポートします。|  
|QuickInfo|REG\_DWORD|0\-1|Intellisense によるクイック ヒントの操作をサポートします。|  
|ShowMatchingBrace|REG\_DWORD|0\-1|ステータス バーに一致する言語のペアを表示するためのサポート。|  
|MatchBracesAtCaret|REG\_DWORD|0\-1|使用する 2 つの要素を強調表示の一致する言語の組み合わせを表示するためのサポート。|  
|MaxErrorMessages|REG\_DWORD|0 ~ n|表示できるエラーの最大数、 **エラー一覧** ウィンドウです。|  
|CodeSenseDelay|REG\_DWORD|0 ~ n|IntelliSense 操作の解析中、色の背景を開始する前に遅延時間をミリ秒数。|  
|EnableAsyncCompletion|REG\_DWORD|0\-1|バック グラウンドの解析をサポートします。|  
|EnableCommenting|REG\_DWORD|0\-1|選択したテキスト ブロックをコメント アウトのサポート、選択したテキストをコメント解除のサポートも含まれる。|  
|EnableFormatSelection|REG\_DWORD|0\-1|自動インデントなどのテキストの書式設定または中かっこの位置の調整をサポート。|  
|AutoOutlining|REG\_DWORD|0\-1|アウトライン \(縮小可能な領域\) をサポートします。|  
|MaxRegions|REG\_DWORD|0 ~ n|ファイルごとに非表示の領域の最大数。|  
  
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
  
## 参照  
 [言語サービスを開発します。](../../extensibility/internals/developing-a-legacy-language-service.md)