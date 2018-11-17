---
title: IDiaSymbol |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol interface
ms.assetid: 01ad328a-736c-4933-a9f8-c2ded19ddd8c
caps.latest.revision: 33
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2bd52443d4150b371bbaa1865978db9a72c5c616
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51734147"
---
# <a name="idiasymbol"></a>IDiaSymbol
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

シンボルのインスタンスのプロパティについて説明します。  
  
## <a name="syntax"></a>構文  
  
```  
IDiaSymbol : IUnknown  
```  
  
## <a name="methods-in-alphabetical-order"></a>アルファベット順にメソッド  
 次の表は、メソッドの`IDiaSymbol`します。  
  
> [!NOTE]
>  シンボルはシンボルの種類に応じて、これらのメソッドの一部のみに対して意味のあるデータを返します。 メソッドから返された場合`S_OK`、そのメソッドには意味のあるデータが返されます。  
  
|メソッド|説明|  
|------------|-----------------|  
|[IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)|シンボルのすべての子を取得します。|  
|[IDiaSymbol::findChildrenEx](../../debugger/debug-interface-access/idiasymbol-findchildrenex.md)|シンボルの子を取得します。 このメソッドは、拡張のバージョンの[idiasymbol::findchildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)します。|  
|[IDiaSymbol::findChildrenExByAddr](../../debugger/debug-interface-access/idiasymbol-findchildrenexbyaddr.md)|指定したアドレスに有効なシンボルの子を取得します。|  
|[IDiaSymbol::findChildrenExByRVA](../../debugger/debug-interface-access/idiasymbol-findchildrenexbyrva.md)|指定された相対仮想アドレス (RVA) で有効なシンボルの子を取得します。|  
|[IDiaSymbol::findChildrenExByVA](../../debugger/debug-interface-access/idiasymbol-findchildrenexbyva.md)|指定された仮想アドレスで有効なシンボルの子を取得します。|  
|[IDiaSymbol::findInlineFramesByAddr](../../debugger/debug-interface-access/idiasymbol-findinlineframesbyaddr.md)|により、クライアントは、すべての指定したアドレスにインライン フレームを反復処理する列挙体を取得します。|  
|[IDiaSymbol::findInlineFramesByRVA](../../debugger/debug-interface-access/idiasymbol-findinlineframesbyrva.md)|により、クライアントは、すべての指定された相対仮想アドレス (RVA) でのインライン フレームを反復処理する列挙体を取得します。|  
|[IDiaSymbol::findInlineFramesByVA](../../debugger/debug-interface-access/idiasymbol-findinlineframesbyva.md)|により、クライアントは、すべての指定した仮想アドレス (VA) にインライン フレームを反復処理する列挙体を取得します。|  
|[IDiaSymbol::findInlineeLines](../../debugger/debug-interface-access/idiasymbol-findinlineelines.md)|により、クライアントは直接、インライン展開はすべての関数または間接的には、この記号の行の番号情報を反復処理する列挙体を取得します。|  
|[IDiaSymbol::findInlineeLinesByAddr](../../debugger/debug-interface-access/idiasymbol-findinlineelinesbyaddr.md)|により、クライアントは、行番号の情報がインライン展開されて、直接または間接的に、この記号を指定したアドレスの範囲内のすべての関数を反復処理する列挙体を取得します。|  
|[IDiaSymbol::findInlineeLinesByRVA](../../debugger/debug-interface-access/idiasymbol-findinlineelinesbyrva.md)|により、クライアントは、行番号の情報がインライン展開されて、直接または間接的に、指定された相対仮想アドレス (RVA) 内でこのシンボルのすべての関数を反復処理する列挙体を取得します。|  
|[IDiaSymbol::findInlineeLinesByVA](../../debugger/debug-interface-access/idiasymbol-findinlineelinesbyva.md)|により、クライアントは、行番号の情報がインライン展開されて、直接または間接的に、この記号を指定した仮想アドレス (VA) 内のすべての関数を反復処理する列挙体を取得します。|  
|[IDiaSymbol::findSymbolsByRVAForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasymbol-findsymbolsbyrvaforacceleratorpointertag.md)|対応するタグの値を指定すると、このメソッドは、指定の相対仮想アドレスにある場合は、このスタブ関数に含まれているシンボルの列挙体を返します。|  
|[IDiaSymbol::findSymbolsForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasymbol-findsymbolsforacceleratorpointertag.md)|C++ AMP のスタブ関数では、アクセラレータのポインターのタグの数を返します。|  
|[IDiaSymbol::get_acceleratorPointerTags](../../debugger/debug-interface-access/idiasymbol-get-acceleratorpointertags.md)|C++ AMP のアクセラレータのスタブ関数に対応するすべてのアクセラレータ ポインター タグ値を返します。|  
|[IDiaSymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)|クラス メンバーのアクセス修飾子を取得します。|  
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|アドレス場所のオフセットの部分を取得します。|  
|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|アドレス場所のセクションの一部を取得します。|  
|[IDiaSymbol::get_addressTaken](../../debugger/debug-interface-access/idiasymbol-get-addresstaken.md)|別のシンボルがこのアドレスを参照するかどうかを示すフラグを取得します。|  
|[IDiaSymbol::get_age](../../debugger/debug-interface-access/idiasymbol-get-age.md)|プログラム データベースの有効期間の値を取得します。|  
|[IDiaSymbol::get_arrayIndexType](../../debugger/debug-interface-access/idiasymbol-get-arrayindextype.md)|配列のインデックスの種類のシンボルの識別子を取得します。|  
|[IDiaSymbol::get_arrayIndexTypeId](../../debugger/debug-interface-access/idiasymbol-get-arrayindextypeid.md)|シンボルの配列インデックスの種類の識別子を取得します。|  
|[IDiaSymbol::get_backEndMajor](../../debugger/debug-interface-access/idiasymbol-get-backendmajor.md)|バック エンドのメジャー バージョン番号を取得します。|  
|[IDiaSymbol::get_backEndMinor](../../debugger/debug-interface-access/idiasymbol-get-backendminor.md)|バック エンドのマイナー バージョン番号を取得します。|  
|[IDiaSymbol::get_backEndBuild](../../debugger/debug-interface-access/idiasymbol-get-backendbuild.md)|バックエンドのビルド番号を取得します。|  
|[IDiaSymbol::get_baseDataOffset](../../debugger/debug-interface-access/idiasymbol-get-basedataoffset.md)|基本データ オフセットを取得します。|  
|[IDiaSymbol::get_baseDataSlot](../../debugger/debug-interface-access/idiasymbol-get-basedataslot.md)|基本データ スロットを取得します。|  
|[IDiaSymbol::get_baseSymbol](../../debugger/debug-interface-access/idiasymbol-get-basesymbol.md)|ポインターを基づいてシンボルを取得します。|  
|[IDiaSymbol::get_baseSymbolId](../../debugger/debug-interface-access/idiasymbol-get-basesymbolid.md)|ポインターを基づいてシンボル ID を取得します。|  
|[IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)|単純型の型のタグを取得します。|  
|[IDiaSymbol::get_bitPosition](../../debugger/debug-interface-access/idiasymbol-get-bitposition.md)|位置のビット位置を取得します。|  
|[IDiaSymbol::get_builtInKind](../../debugger/debug-interface-access/idiasymbol-get-builtinkind.md)|HLSL 型の組み込みの種類を取得します。|  
|[IDiaSymbol::get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)|メソッドの呼び出し規約を示すインジケーターを返します。|  
|[IDiaSymbol::get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)|シンボルのクラスの親への参照を取得します。|  
|[IDiaSymbol::get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)|シンボルのクラスの親識別子を取得します。|  
|[IDiaSymbol::get_code](../../debugger/debug-interface-access/idiasymbol-get-code.md)|シンボルがコードのアドレスを参照するかどうかを示すフラグを取得します。|  
|[IDiaSymbol::get_compilerGenerated](../../debugger/debug-interface-access/idiasymbol-get-compilergenerated.md)|コンパイラによって生成されたシンボルであったかどうかを示すフラグを取得します。|  
|[IDiaSymbol::get_compilerName](../../debugger/debug-interface-access/idiasymbol-get-compilername.md)|作成に使用されるコンパイラの名前を取得、[コンパイル単位](../../debugger/debug-interface-access/compiland.md)します。|  
|[IDiaSymbol::get_constructor](../../debugger/debug-interface-access/idiasymbol-get-constructor.md)|ユーザー定義データ型にコンス トラクターがあるかどうかを示すフラグを取得します。|  
|[IDiaSymbol::get_container](../../debugger/debug-interface-access/idiasymbol-get-container.md)|この記号の含まれているシンボルを取得します。|  
|[IDiaSymbol::get_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|ユーザー定義データ型が定数かどうかを示すフラグを取得します。|  
|[IDiaSymbol::get_count](../../debugger/debug-interface-access/idiasymbol-get-count.md)|リストまたは配列内の項目の数を取得します。|  
|[IDiaSymbol::get_countLiveRanges](../../debugger/debug-interface-access/idiasymbol-get-countliveranges.md)|ローカル シンボルに関連付けられている有効なアドレス範囲の数を取得します。|  
|[IDiaSymbol::get_customCallingConvention](../../debugger/debug-interface-access/idiasymbol-get-customcallingconvention.md)|関数は、カスタム呼び出し規約を使用するかどうかを示すフラグを取得します。|  
|[IDiaSymbol::get_dataBytes](../../debugger/debug-interface-access/idiasymbol-get-databytes.md)|OEM 記号のデータ バイトを取得します。|  
|[IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)|データ シンボルの変数の分類を取得します。|  
|[IDiaSymbol::get_editAndContinueEnabled](../../debugger/debug-interface-access/idiasymbol-get-editandcontinueenabled.md)|コンパイル済みプログラムまたは単位のエディット コンティニュの機能を記述するフラグを取得します。|  
|[IDiaSymbol::get_farReturn](../../debugger/debug-interface-access/idiasymbol-get-farreturn.md)|関数ははるかに戻り値を使用するかどうかを示すフラグを取得します。|  
|[IDiaSymbol::get_frontEndMajor](../../debugger/debug-interface-access/idiasymbol-get-frontendmajor.md)|フロント エンドのメジャー バージョン番号を取得します。|  
|[IDiaSymbol::get_frontEndMinor](../../debugger/debug-interface-access/idiasymbol-get-frontendminor.md)|フロント エンドのマイナー バージョン番号を取得します。|  
|[IDiaSymbol::get_frontEndBuild](../../debugger/debug-interface-access/idiasymbol-get-frontendbuild.md)|フロント エンドのビルド番号を取得します。|  
|[IDiaSymbol::get_function](../../debugger/debug-interface-access/idiasymbol-get-function.md)|パブリック シンボルが関数を参照するかどうかを示すフラグを取得します。|  
|[IDiaSymbol::get_guid](../../debugger/debug-interface-access/idiasymbol-get-guid.md)|シンボルの GUID を取得します。|  
|[IDiaSymbol::get_hasAlloca](../../debugger/debug-interface-access/idiasymbol-get-hasalloca.md)|関数への呼び出しが含まれるかどうかを示すフラグを取得します。`alloca`します。|  
|[IDiaSymbol::get_hasAssignmentOperator](../../debugger/debug-interface-access/idiasymbol-get-hasassignmentoperator.md)|ユーザー定義データ型が定義されている任意の代入演算子を持つかどうかを示すフラグを取得します。|  
|[IDiaSymbol::get_hasCastOperator](../../debugger/debug-interface-access/idiasymbol-get-hascastoperator.md)|ユーザー定義データ型が定義されているすべてのキャスト演算子を持つかどうかを示すフラグを取得します。|  
|[IDiaSymbol::get_hasDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-hasdebuginfo.md)|コンパイル単位がデバッグ情報を格納しているかどうかを示すフラグを取得します。|  
|[IDiaSymbol::get_hasEH](../../debugger/debug-interface-access/idiasymbol-get-haseh.md)|関数が C++ スタイルの例外ハンドラーであるかどうかを示すフラグを取得します。|  
|[IDiaSymbol::get_hasEHa](../../debugger/debug-interface-access/idiasymbol-get-haseha.md)|関数は、非同期の例外ハンドラーがあるかどうかを示すフラグを取得します。|  
|[IDiaSymbol::get_hasInlAsm](../../debugger/debug-interface-access/idiasymbol-get-hasinlasm.md)|関数はインライン アセンブリであるかどうかを示すフラグを取得します。|  
|[IDiaSymbol::get_hasLongJump](../../debugger/debug-interface-access/idiasymbol-get-haslongjump.md)|Longjmp コマンド (C スタイルの例外処理の一部) が関数に含まれるかどうかを示すフラグを取得します。|  
|[IDiaSymbol::get_hasManagedCode](../../debugger/debug-interface-access/idiasymbol-get-hasmanagedcode.md)|マネージ コードが、モジュールに含まれるかどうかを示すフラグを取得します。|  
|[IDiaSymbol::get_hasNestedTypes](../../debugger/debug-interface-access/idiasymbol-get-hasnestedtypes.md)|ユーザー定義データ型の種類の定義に入れ子になったかどうかを示すフラグを取得します。|  
|[IDiaSymbol::get_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|関数またはコンパイル単位でコンパイルされたセキュリティ チェックがあるかどうかを示すフラグを取得します (を使用して、 [/GS (バッファー セキュリティ チェック)](http://msdn.microsoft.com/library/8d8a5ea1-cd5e-42e1-bc36-66e1cd7e731e)コンパイラ スイッチ)。|  
|[IDiaSymbol::get_hasSEH](../../debugger/debug-interface-access/idiasymbol-get-hasseh.md)|関数では、Win32 スタイルの構造化例外処理があるかどうかを示すフラグを取得します。|  
|[IDiaSymbol::get_hasSetJump](../../debugger/debug-interface-access/idiasymbol-get-hassetjump.md)|Setjmp コマンドが、関数に含まれるかどうかを示すフラグを取得します。|  
|[IDiaSymbol::get_indirectVirtualBaseClass](../../debugger/debug-interface-access/idiasymbol-get-indirectvirtualbaseclass.md)|ユーザー定義データ型が間接仮想基底クラスであるかどうかを示すフラグを取得します。|  
|[IDiaSymbol::get_InlSpec](../../debugger/debug-interface-access/idiasymbol-get-inlspec.md)|関数がインライン属性でマークされているかどうかを示すフラグを取得します。|  
|[IDiaSymbol::get_interruptReturn](../../debugger/debug-interface-access/idiasymbol-get-interruptreturn.md)|関数に割り込み命令からの戻り値があるかどうかを示すフラグを取得します。|  
|[IDiaSymbol::get_intro](../../debugger/debug-interface-access/idiasymbol-get-intro.md)|関数が基底クラスの仮想関数であるかどうかを示すフラグを取得します。|  
|[IDiaSymbol::get_isAcceleratorGroupSharedLocal](../../debugger/debug-interface-access/idiasymbol-get-isacceleratorgroupsharedlocal.md)|C++ AMP のアクセラレータのコンパイルされたコードでグループの共有ローカル変数に、シンボルが対応かどうかを示すフラグを取得します。|  
|[IDiaSymbol::get_isAcceleratorPointerTagLiveRange](../../debugger/debug-interface-access/idiasymbol-get-isacceleratorpointertagliverange.md)|シンボルに対応するかどうかを示すフラグを取得、*定義範囲シンボル*C++ AMP のアクセラレータのコンパイルされたコードでポインター変数のタグの要素。 定義の範囲のシンボルは、アドレスの範囲の変数の場所です。|  
|[IDiaSymbol::get_isAcceleratorStubFunction](../../debugger/debug-interface-access/idiasymbol-get-isacceleratorstubfunction.md)|シェーダーに対応するアクセラレータのコンパイルのシンボルが最上位の関数シンボルに対応するかどうかを示す、`parallel_for_each`呼び出します。|  
|[IDiaSymbol::get_isAggregated](../../debugger/debug-interface-access/idiasymbol-get-isaggregated.md)|データが多数のシンボルの集計の一部であるかどうかを示すフラグを取得します。|  
|[IDiaSymbol::get_isCTypes](../../debugger/debug-interface-access/idiasymbol-get-isctypes.md)|シンボル ファイルが C の型を含むかどうかを示すフラグを取得します。|  
|[IDiaSymbol::get_isCVTCIL](../../debugger/debug-interface-access/idiasymbol-get-iscvtcil.md)|モジュールが共通中間言語 (CIL) からをネイティブ コードに変換されたかどうかを示すフラグを取得します。|  
|[IDiaSymbol::get_isDataAligned](../../debugger/debug-interface-access/idiasymbol-get-isdataaligned.md)|ユーザー定義データ型の要素を特定の境界に配置するかどうかを示すフラグを取得します。|  
|[IDiaSymbol::get_isHLSLData](../../debugger/debug-interface-access/idiasymbol-get-ishlsldata.md)|このシンボルが上位レベル シェーダー言語 (HLSL) のデータを表すかどうかを指定します。|  
|[IDiaSymbol::get_isHotpatchable](../../debugger/debug-interface-access/idiasymbol-get-ishotpatchable.md)|モジュールをコンパイルしたかどうかを示すフラグを取得、 [/hotpatch (ホットパッチ可能なイメージの作成)](http://msdn.microsoft.com/library/aad539b6-c053-4c78-8682-853d98327798)コンパイラ スイッチ。|  
|[IDiaSymbol::get_isLTCG](../../debugger/debug-interface-access/idiasymbol-get-isltcg.md)|リンカーの LTCG にマネージ コンパイル単位がリンクされているかどうかを示すフラグを取得します。|  
|[IDiaSymbol::get_isMatrixRowMajor](../../debugger/debug-interface-access/idiasymbol-get-ismatrixrowmajor.md)|マトリックスが主要な行であるかどうかを指定します。|  
|[IDiaSymbol::get_isMSILNetmodule](../../debugger/debug-interface-access/idiasymbol-get-ismsilnetmodule.md)|マネージ コンパイル単位が、.netmodule を (メタデータのみを含む) であるかどうかを示すフラグを取得します。|  
|[IDiaSymbol::get_isMultipleInheritance](../../debugger/debug-interface-access/idiasymbol-get-ismultipleinheritance.md)|指定するかどうか、`this`多重継承を持つデータ メンバーを指すポインター。|  
|[IDiaSymbol::get_isNaked](../../debugger/debug-interface-access/idiasymbol-get-isnaked.md)|関数があるかどうかを示すフラグを取得、 [naked](http://msdn.microsoft.com/library/69723241-05e1-439b-868e-20a83a16ab6d)属性。|  
|[IDiaSymbol::get_isOptimizedAway](../../debugger/debug-interface-access/idiasymbol-get-isoptimizedaway.md)|変数が最適化に機能しているかどうかを指定します。|  
|[IDiaSymbol::get_isPointerBasedOnSymbolValue](../../debugger/debug-interface-access/idiasymbol-get-ispointerbasedonsymbolvalue.md)|指定するかどうか、`this`ポインターがシンボル値に基づきます。|  
|[IDiaSymbol::get_isPointerToDataMember](../../debugger/debug-interface-access/idiasymbol-get-ispointertodatamember.md)|このシンボルがデータ メンバーへのポインターであるかどうかを指定します。|  
|[IDiaSymbol::get_isPointerToMemberFunction](../../debugger/debug-interface-access/idiasymbol-get-ispointertomemberfunction.md)|このシンボルがメンバー関数へのポインターであるかどうかを指定します。|  
|[IDiaSymbol::get_isReturnValue](../../debugger/debug-interface-access/idiasymbol-get-isreturnvalue.md)|変数は戻り値の値を保持するかどうかを指定します。|  
|[IDiaSymbol::get_isSdl](../../debugger/debug-interface-access/idiasymbol-get-issdl.md)|/SDL オプションを使用して、モジュールをコンパイルするかどうかを指定します。|  
|[IDiaSymbol::get_isSingleInheritance](../../debugger/debug-interface-access/idiasymbol-get-issingleinheritance.md)|指定するかどうか、`this`単一継承を持つデータ メンバーを指すポインター。|  
|[IDiaSymbol::get_isSplitted](../../debugger/debug-interface-access/idiasymbol-get-issplitted.md)|データを個別のシンボルの集計に分割されて かどうかを示すフラグを取得します。|  
|[IDiaSymbol::get_isStatic](../../debugger/debug-interface-access/idiasymbol-get-isstatic.md)|関数またはサンクのレイヤーが静的かどうかを示すフラグを取得します。|  
|[IDiaSymbol::get_isStripped](../../debugger/debug-interface-access/idiasymbol-get-isstripped.md)|プライベート シンボルがシンボル ファイルから削除されたかどうかを示すフラグを取得します。|  
|[IDiaSymbol::get_isVirtualInheritance](../../debugger/debug-interface-access/idiasymbol-get-isvirtualinheritance.md)|指定するかどうか、`this`仮想継承を持つデータ メンバーを指すポインター。|  
|[IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)|ソースの言語を取得します。|  
|[IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|この記号によって表されるオブジェクトによって使用されるメモリのバイト数を取得します。|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|シンボルの構文の親への参照を取得します。|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|シンボルの構文の親識別子を取得します。|  
|[IDiaSymbol::get_libraryName](../../debugger/debug-interface-access/idiasymbol-get-libraryname.md)|オブジェクトの読み込み元のライブラリまたはオブジェクトのファイルのファイル名を取得します。|  
|[IDiaSymbol::get_liveRangeLength](../../debugger/debug-interface-access/idiasymbol-get-liverangelength.md)|ローカル シンボルの有効なアドレスの範囲の長さを返します。|  
|[IDiaSymbol::get_liveRangeStartAddressSection](../../debugger/debug-interface-access/idiasymbol-get-liverangestartaddresssection.md)|ローカル シンボルの有効なアドレス範囲の開始のセクションの一部を返します。|  
|[IDiaSymbol::get_liveRangeStartAddressOffset](../../debugger/debug-interface-access/idiasymbol-get-liverangestartaddressoffset.md)|ローカル シンボルの有効なアドレス範囲の開始のオフセットの部分を返します。|  
|[IDiaSymbol::get_liveRangeStartRelativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-liverangestartrelativevirtualaddress.md)|ローカル シンボルの有効なアドレスの範囲の開始を返します。|  
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|データ シンボルの場所の種類を取得します。|  
|[IDiaSymbol::get_lowerBound](../../debugger/debug-interface-access/idiasymbol-get-lowerbound.md)|FORTRAN 配列の次元の下限を取得します。|  
|[IDiaSymbol::get_lowerBoundId](../../debugger/debug-interface-access/idiasymbol-get-lowerboundid.md)|FORTRAN 配列の次元の下限の境界のシンボルの識別子を取得します。|  
|[IDiaSymbol::get_machineType](../../debugger/debug-interface-access/idiasymbol-get-machinetype.md)|ターゲット CPU の種類を取得します。|  
|[IDiaSymbol::get_managed](../../debugger/debug-interface-access/idiasymbol-get-managed.md)|シンボルが参照するかどうかを示すコードの管理されているフラグを取得します。|  
|[IDiaSymbol::get_memorySpaceKind](../../debugger/debug-interface-access/idiasymbol-get-memoryspacekind.md)|メモリ領域の種類を取得します。|  
|[IDiaSymbol::get_msil](../../debugger/debug-interface-access/idiasymbol-get-msil.md)|Microsoft Intermediate Language (MSIL) コードをシンボルが参照するかどうかを示すフラグを取得します。|  
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|シンボルの名前を取得します。|  
|[IDiaSymbol::get_nested](../../debugger/debug-interface-access/idiasymbol-get-nested.md)|ユーザー定義データ型が入れ子になっているかどうかを示すフラグを取得します。|  
|[IDiaSymbol::get_noInline](../../debugger/debug-interface-access/idiasymbol-get-noinline.md)|関数が付いているかどうかを示すフラグを取得、 [noinline](http://msdn.microsoft.com/library/f259d55b-dec7-4bde-8cf9-14521e4fdc42)属性。|  
|[IDiaSymbol::get_noReturn](../../debugger/debug-interface-access/idiasymbol-get-noreturn.md)|関数が宣言されているかどうかを示すフラグを取得、 [noreturn](http://msdn.microsoft.com/library/9c6517e5-22d7-4051-9974-3d2200ae4d1d)属性。|  
|[IDiaSymbol::get_noStackOrdering](../../debugger/debug-interface-access/idiasymbol-get-nostackordering.md)|スタックの順序付けでしたを実行できるかスタック バッファーのチェックの一部としてを示すフラグを取得しません。|  
|[IDiaSymbol::get_notReached](../../debugger/debug-interface-access/idiasymbol-get-notreached.md)|関数またはラベルに達することはないかどうかを示すフラグを取得します。|  
|[IDiaSymbol::get_numberOfAcceleratorPointerTags](../../debugger/debug-interface-access/idiasymbol-get-numberofacceleratorpointertags.md)|C++ AMP のスタブ関数では、アクセラレータのポインターのタグの数を返します。|  
|[IDiaSymbol::get_numberOfModifiers](../../debugger/debug-interface-access/idiasymbol-get-numberofmodifiers.md)|元の型に適用されている修飾子の数を取得します。|  
|[IDiaSymbol::get_numberOfRegisterIndices](../../debugger/debug-interface-access/idiasymbol-get-numberofregisterindices.md)|レジスタのインデックスの数を取得します。|  
|[IDiaSymbol::get_numberOfRows](../../debugger/debug-interface-access/idiasymbol-get-numberofrows.md)|マトリックス内の行の数を取得します。|  
|[IDiaSymbol::get_numberOfColumns](../../debugger/debug-interface-access/idiasymbol-get-numberofcolumns.md)|マトリックスの列の数を取得します。|  
|[IDiaSymbol::get_objectFileName](../../debugger/debug-interface-access/idiasymbol-get-objectfilename.md)|オブジェクト ファイルの名前を取得します。|  
|[IDiaSymbol::get_objectPointerType](../../debugger/debug-interface-access/idiasymbol-get-objectpointertype.md)|クラスのメソッドのオブジェクトへのポインターの種類を取得します。|  
|[IDiaSymbol::get_oemId](../../debugger/debug-interface-access/idiasymbol-get-oemid.md)|シンボルの取得`oemId`値。|  
|[IDiaSymbol::get_oemSymbolId](../../debugger/debug-interface-access/idiasymbol-get-oemsymbolid.md)|シンボルの取得`oemSymbolId`値。|  
|[IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|シンボルの場所のオフセットを取得します。|  
|[IDiaSymbol::get_optimizedCodeDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-optimizedcodedebuginfo.md)|関数またはラベルに最適化されたコードが含まれているかどうかを示すフラグの取得も同様のデバッグ情報。|  
|[IDiaSymbol::get_overloadedOperator](../../debugger/debug-interface-access/idiasymbol-get-overloadedoperator.md)|ユーザー定義データ型が演算子をオーバー ロードされたかどうかを示すフラグを取得します。|  
|[IDiaSymbol::get_packed](../../debugger/debug-interface-access/idiasymbol-get-packed.md)|ユーザー定義データ型がパックされているかどうかを示すフラグを取得します。|  
|[IDiaSymbol::get_platform](../../debugger/debug-interface-access/idiasymbol-get-platform.md)|コンパイル単位、プログラムのコンパイルされた対象のプラットフォームの種類を取得します。|  
|[IDiaSymbol::get_pure](../../debugger/debug-interface-access/idiasymbol-get-pure.md)|関数が純粋なかどうかを示すフラグを取得する仮想です。|  
|[IDiaSymbol::get_rank](../../debugger/debug-interface-access/idiasymbol-get-rank.md)|FORTRAN の多次元配列のランクを取得します。|  
|[IDiaSymbol::get_reference](../../debugger/debug-interface-access/idiasymbol-get-reference.md)|ポインター型が参照するかどうかを示すフラグを取得します。|  
|[IDiaSymbol::get_registerId](../../debugger/debug-interface-access/idiasymbol-get-registerid.md)|場所のレジスタの指定子を取得します。|  
|[IDiaSymbol::get_registerType](../../debugger/debug-interface-access/idiasymbol-get-registertype.md)|Register 型を取得します。|  
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|場所の相対仮想アドレス (RVA) を取得します。|  
|[IDiaSymbol::get_restrictedType](../../debugger/debug-interface-access/idiasymbol-get-restrictedtype.md)|指定するかどうか、`this`ポインターがフラグが設定された制限付きとします。|  
|[IDiaSymbol::get_samplerSlot](../../debugger/debug-interface-access/idiasymbol-get-samplerslot.md)|サンプラーのスロットを取得します。|  
|[IDiaSymbol::get_scoped](../../debugger/debug-interface-access/idiasymbol-get-scoped.md)|非グローバルな構文のスコープで、ユーザー定義データ型を表示するかどうかを示すフラグを取得します。|  
|[IDiaSymbol::get_signature](../../debugger/debug-interface-access/idiasymbol-get-signature.md)|シンボルのシグネチャの値を取得します。|  
|[IDiaSymbol::get_sizeInUdt](../../debugger/debug-interface-access/idiasymbol-get-sizeinudt.md)|ユーザー定義型のメンバーのサイズを取得します。|  
|[IDiaSymbol::get_slot](../../debugger/debug-interface-access/idiasymbol-get-slot.md)|場所のスロット番号を取得します。|  
|[IDiaSymbol::get_sourceFileName](../../debugger/debug-interface-access/idiasymbol-get-sourcefilename.md)|ソース ファイルのファイル名を取得します。|  
|[IDiaSymbol::getSrcLineOnTypeDefn](../../debugger/debug-interface-access/idiasymbol-getsrclineontypedefn.md)|指定されたユーザー定義型が定義されているかを示すソース ファイルと行番号を取得します。|  
|[IDiaSymbol::get_stride](../../debugger/debug-interface-access/idiasymbol-get-stride.md)|マトリックスまたは strided 配列のストライドを取得します。|  
|[IDiaSymbol::get_subType](../../debugger/debug-interface-access/idiasymbol-get-subtype.md)|サブ タイプを取得します。|  
|[IDiaSymbol::get_subTypeId](../../debugger/debug-interface-access/idiasymbol-get-subtypeid.md)|Sub 型 ID を取得します。|  
|[IDiaSymbol::get_symbolsFileName](../../debugger/debug-interface-access/idiasymbol-get-symbolsfilename.md)|シンボルが読み込まれた元のファイルの名前を取得します。|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|シンボルの一意の識別子を取得します。|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|シンボル型の分類子を取得します。|  
|[IDiaSymbol::get_targetOffset](../../debugger/debug-interface-access/idiasymbol-get-targetoffset.md)|サンク ターゲットのオフセット セクションを取得します。|  
|[IDiaSymbol::get_targetRelativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-targetrelativevirtualaddress.md)|サンク ターゲットの相対仮想アドレス (RVA) を取得します。|  
|[IDiaSymbol::get_targetSection](../../debugger/debug-interface-access/idiasymbol-get-targetsection.md)|サンク ターゲットのアドレス セクションを取得します。|  
|[IDiaSymbol::get_targetVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-targetvirtualaddress.md)|サンク ターゲットの仮想アドレス (VA) を取得します。|  
|[IDiaSymbol::get_textureSlot](../../debugger/debug-interface-access/idiasymbol-get-textureslot.md)|テクスチャのスロットを取得します。|  
|[IDiaSymbol::get_thisAdjust](../../debugger/debug-interface-access/idiasymbol-get-thisadjust.md)|論理取得`this`調整メソッドの権限を保持します。|  
|[IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)|関数のサンクの型を取得します。|  
|[IDiaSymbol::get_timeStamp](../../debugger/debug-interface-access/idiasymbol-get-timestamp.md)|基になる実行可能ファイルのタイムスタンプを取得します。|  
|[IDiaSymbol::get_token](../../debugger/debug-interface-access/idiasymbol-get-token.md)|マネージ関数または変数のメタデータ トークンを取得します。|  
|[IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|関数シグネチャへの参照を取得します。|  
|[IDiaSymbol::get_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|シンボルの型の識別子を取得します。|  
|[IDiaSymbol::get_types](../../debugger/debug-interface-access/idiasymbol-get-types.md)|このシンボルのコンパイラ固有の型の値の配列を取得します。|  
|[IDiaSymbol::get_typeIds](../../debugger/debug-interface-access/idiasymbol-get-typeids.md)|このシンボルのコンパイラ固有の型識別子の値の配列を取得します。|  
|[IDiaSymbol::get_uavSlot](../../debugger/debug-interface-access/idiasymbol-get-uavslot.md)|Uav スロットを取得します。|  
|[IDiaSymbol::get_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md)|さまざまなユーザー定義型 (UDT) を取得します。|  
|[IDiaSymbol::get_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|ユーザー定義データ型が整列されていないかどうかを示すフラグを取得します。|  
|[IDiaSymbol::get_undecoratedName](../../debugger/debug-interface-access/idiasymbol-get-undecoratedname.md)|C++ の装飾、またはリンケージ、名前の非装飾名を取得します。|  
|[IDiaSymbol::get_undecoratedNameEx](../../debugger/debug-interface-access/idiasymbol-get-undecoratednameex.md)|拡張機能、`get_undecoratedName`拡張フィールドの値に基づく非装飾名を取得するメソッド。|  
|[IDiaSymbol::get_unmodifiedTypeId](../../debugger/debug-interface-access/idiasymbol-get-unmodifiedtypeid.md)|元の (変更なし) の型の ID を取得します。|  
|[IDiaSymbol::get_upperBound](../../debugger/debug-interface-access/idiasymbol-get-upperbound.md)|FORTRAN 配列の次元の上限を取得します。|  
|[IDiaSymbol::get_upperBoundId](../../debugger/debug-interface-access/idiasymbol-get-upperboundid.md)|FORTRAN 配列の次元の上限のシンボルの識別子を取得します。|  
|[IDiaSymbol::get_value](../../debugger/debug-interface-access/idiasymbol-get-value.md)|定数の値を取得します。|  
|[IDiaSymbol::get_virtual](../../debugger/debug-interface-access/idiasymbol-get-virtual.md)|関数が仮想かどうかを示すフラグを取得します。|  
|[IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|場所の仮想アドレス (VA) を取得します。|  
|[IDiaSymbol::get_virtualBaseClass](../../debugger/debug-interface-access/idiasymbol-get-virtualbaseclass.md)|ユーザー定義データ型が仮想基底クラスかどうかを示すフラグを取得します。|  
|[IDiaSymbol::get_virtualBaseDispIndex](../../debugger/debug-interface-access/idiasymbol-get-virtualbasedispindex.md)|仮想基本変位テーブルにインデックスを取得します。|  
|[IDiaSymbol::get_virtualBaseOffset](../../debugger/debug-interface-access/idiasymbol-get-virtualbaseoffset.md)|仮想関数の仮想関数テーブル内のオフセットを取得します。|  
|[IDiaSymbol::get_virtualBasePointerOffset](../../debugger/debug-interface-access/idiasymbol-get-virtualbasepointeroffset.md)|仮想基底ポインターのオフセットを取得します。|  
|[IDiaSymbol::get_virtualBaseTableType](../../debugger/debug-interface-access/idiasymbol-get-virtualbasetabletype.md)|仮想ベース テーブルのポインターの型を取得します。|  
|[IDiaSymbol::get_virtualTableShape](../../debugger/debug-interface-access/idiasymbol-get-virtualtableshape.md)|ユーザー定義型の仮想テーブルの型のシンボルのインターフェイスを取得します。|  
|[IDiaSymbol::get_virtualTableShapeId](../../debugger/debug-interface-access/idiasymbol-get-virtualtableshapeid.md)|シンボルの仮想テーブル シェイプの id を取得します。|  
|[IDiaSymbol::get_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|ユーザー定義データ型が volatile かどうかを示すフラグを取得します。|  
  
## <a name="remarks"></a>Remarks  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 次の方法の 1 つを呼び出すことによってこのインターフェイスを取得します。  
  
-   [IDiaEnumSymbols::Item](../../debugger/debug-interface-access/idiaenumsymbols-item.md)  
  
-   [IDiaEnumSymbols::Next](../../debugger/debug-interface-access/idiaenumsymbols-next.md)  
  
-   [IDiaEnumSymbolsByAddr::Next](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-next.md)  
  
-   [IDiaEnumSymbolsByAddr::Prev](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-prev.md)  
  
-   [IDiaEnumSymbolsByAddr::symbolByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyaddr.md)  
  
-   [IDiaEnumSymbolsByAddr::symbolByRVA](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyrva.md)  
  
-   [IDiaEnumSymbolsByAddr::symbolByVA](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyva.md)  
  
-   [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)  
  
-   [IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)  
  
-   [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)  
  
-   [IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)  
  
-   [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)  
  
-   [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)  
  
-   [IDiaSession::symbolById](../../debugger/debug-interface-access/idiasession-symbolbyid.md)  
  
-   [IDiaStackWalkHelper::symbolForVA](../../debugger/debug-interface-access/idiastackwalkhelper-symbolforva.md)  
  
-   [IDiaSymbol::get_types](../../debugger/debug-interface-access/idiasymbol-get-types.md)  
  
## <a name="example"></a>例  
 この例では、指定の相対仮想アドレスに関数のローカル変数を表示する方法を示します。 また、さまざまな種類のシンボルが相互に関連する方法も説明します。  
  
> [!NOTE]
>  `CDiaBSTR` ラップするクラスは、`BSTR`し、自動的に処理をインスタンス化がスコープから外れたときに、文字列を解放します。  
  
```cpp#  
void DumpLocalVars( DWORD rva, IDiaSession *pSession )  
{  
    CComPtr< IDiaSymbol > pBlock;  
    if ( FAILED( psession->findSymbolByRVA( rva, SymTagBlock, &pBlock ) ) )  
    {  
        Fatal( "Failed to find symbols by RVA" );  
    }  
    CComPtr< IDiaSymbol > pscope;  
    for ( ; pBlock != NULL; )  
    {  
        CComPtr< IDiaEnumSymbols > pEnum;  
        // local data search  
        if ( FAILED( pBlock->findChildren( SymTagNull, NULL, nsNone, &pEnum ) ) )  
        {  
            Fatal( "Local scope findChildren failed" );  
        }  
        CComPtr< IDiaSymbol > pSymbol;  
        DWORD tag;  
        DWORD celt;  
        while ( pEnum != NULL &&  
                SUCCEEDED( pEnum->Next( 1, &pSymbol, &celt ) ) &&  
                celt == 1)  
        {  
            pSymbol->get_symTag( &tag );  
            if ( tag == SymTagData )  
            {  
                CDiaBSTR name;  
                DWORD    kind;  
                pSymbol->get_name( &name );  
                pSymbol->get_dataKind( &kind );  
                if ( name != NULL )  
                    wprintf_s( L"\t%s (%s)\n", name, szDataKinds[ kind ] );  
            }  
            else if ( tag == SymTagAnnotation )  
            {  
                CComPtr< IDiaEnumSymbols > pValues;  
                // local data search  
                wprintf_s( L"\tAnnotation:\n" );  
                if ( FAILED( pSymbol->findChildren( SymTagNull, NULL, nsNone, &pValues ) ) )  
                    Fatal( "Annotation findChildren failed" );  
                pSymbol = NULL;  
                while ( pValues != NULL &&  
                        SUCCEEDED( pValues->Next( 1, &pSymbol, &celt ) ) &&  
                        celt == 1 )  
                {  
                    CComVariant value;  
                    if ( pSymbol->get_value( &value ) != S_OK )  
                        Fatal( "No value for annotation data." );  
                    wprintf_s( L"\t\t%ws\n", value.bstrVal );  
                    pSymbol = NULL;  
                }  
            }  
            pSymbol = NULL;  
        }  
        pBlock->get_symTag( &tag );   
        if ( tag == SymTagFunction )    // stop when at function scope  
            break;  
        // move to lexical parent  
        CComPtr< IDiaSymbol > pParent;  
        if ( SUCCEEDED( pBlock->get_lexicalParent( &pParent ) )  
            && pParent != NULL ) {  
            pBlock = pParent;  
        }  
        else  
        {  
            Fatal( "Finding lexical parent failed." );  
        }  
    };  
}  
```  
  
## <a name="requirements"></a>必要条件  
 `Header:` Dia2.h  
  
 ライブラリ: diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>関連項目  
 [インターフェイス (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [シンボル型のクラス階層](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)   
 [シンボルとシンボル タグ](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)   
 [コンパイル単位](../../debugger/debug-interface-access/compiland.md)



